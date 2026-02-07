---
layout: post
title: "What do Streaming Databases Solve Uniquely?"
---

*This post started from researching recent stream processing solutions like [RisingWave](https://risingwave.com/) and [Materialize](https://materialize.com/). There are some meta-points worth bringing up, so I'm writing them down.*

Why do we need data stream processing in the first place? That's easy - we need to get a hold of fresh data that keep coming into the system. Fresh data are naturally more interesting to us in many aspects of life. "Fresh" is a moving target in terms of absolute timestamps. However, if we anchor it against "now", and express it in "past x hours/days", it is a stable target, only with changing content.

This conceptually makes sense, but why do I need a dedicated stream processing solution? I can simply do on-demand batch queries against my OLAP data warehouse or data lake. They have indexes built on timestamps and other fields, right? This certainly works, and if I don't do too many such queries, it is a viable approach. After all, the type of data that OLAPs would host tend to be billions of rows, tens of TBs, and keeping them as cold (different S3 tiers) as you can tolerate it is a first-order cost concern. Only start building more indexes and caching data to hotter media like SSDs and RAM if you need more frequent and flexible access. So if you keep making a certain kind of queries, OLAPs may rely on some cache and eviction rules to prioritize them. It's the system dynamically responding to your user intent.

<!--more-->

However, if one already knows the fresh part of data is more important to them, they can make this intent explicit, and build solutions that target it. **All the optimizations and tradeoffs can orient themselves around this stable intent as a set of invariants**. Solutions and products in the software ecosystem (and arguably the society at large) follow this rule closely to specialize, from compilers optimizing code, to OLTP vs OLAP, and stream processing is no exception. These invariants serve as anchors and interfaces for people to collaborate towards, and every participant can do a better job with clear specs. From a system perspective, the better we can articulate the invariants as boundaries of something that we want, the better we can fill in the middle to make it fit perfectly. Every once in a while, the messy amalgamation of disjoint components get "reaped" into just a few elegant integrated systems that reflect the user intents more directly. That's a win for the system and a natural evolutionary journey.

Stream processing solutions often materialize the "past x hours/days" queries into views, which formalize the intent that recent data has different value and access patterns than historical data. By explicitly materializing fresh data in a fast-access layer, we can

* Keep hot data in memory or SSD-backed stores
* Push older data into columnar formats optimized for compression and batch queries
* Transition data through tiers as it ages (memory -> SSD -> object storage)

Further, when someone creates a materialized view for "last 24 hours of user activity," they're telling the system: "I will query this repeatedly, optimize accordingly." The system can

* Allocate resources proportional to declared importance
* Skip materialization of unspecified aggregations entirely
* Make different storage/indexing decisions based on the view definition

This allows the additional work to map perfectly to user intents. Contrast this with a pure OLAP store relying on query-driven caching - it's reactive, learns slowly, and wastes resources caching one-off exploratory queries.

Now, what are streaming databases and what do they have on top of stream processing frameworks? RisingWave itself has a [comparison](https://docs.risingwave.com/reference/risingwave-flink-comparison) with Flink that demonstrated its design principles well - the database is the sink where these fresh data materialized views go into, and it's often beneficial to let the very system that writes to it manage it. The invariant from user intent is that they always need a database to host the data, so might as well provide a good one. The additional invariant from the data system is what writes to the database knows the most about the database, and can do further optimizations upholding its promises with a better context.

There is another fine point to the choice of SQL as the user-interface language for both RisingWave and Materialize. Some past stream processing frameworks would use procedural interfaces, DSLs. However, the industry consensus has nominated SQL as the declarative and expressive language to work with tabular data. This is an invariant! Yet again it shows how systems and market players organize themselves around invariants.
