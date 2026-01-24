---
layout: post
title: "What's a \"Senior Engineer\"?"
---

What's a "Senior Engineer"? A senior engineer

- can independently take apart an architectural design spec, and independently drive the parts to completion.
- clarify logical boundaries, inputs/outputs, and vocalize when unclear or blocked, so that project meets minimal blockage during collaboration.
- anticipate, identify bottlenecks during implementation, and find the appropriate algorithmic solutions, to meet latency and throughput requirements.
- has enough fundamental working knowledge and experience, and is able to dive into specifics of core technologies in their stack given a reasonable amount of time, and surgically solve the issue according to well established patterns without them reappearing as compounding complexities.

In some ways, it's easier to check/evaluate a senior person, because there are fewer convergence points that practically every senior person will encounter in their professional lives. For example, a senior systems engineer has to be able to explain and implement a simple hashmap, and explain the various concepts and behaviors. There is no way around it, because without that knowledge, they can't solve a class of problems.

The other side of the coin is, it's harder to evaluate a pre-senior person, because it comes a lot down to individual drive and passion. They shine on a team when they are motivated and can do many things to push the projects forward. It's hard to find those knowledge convergence points to test them during the interviewing process.

Here are some fundamental working knowledge and/or core technologies in different roles.

## Senior Full Stack Engineer

<!--more-->

- JavaScript fundamentals including event loop behavior, closures, and how asynchronous patterns (promises, async/await) affect application performance and user experience
- Proficiency with modern framework ecosystems and state management, understanding when client-side vs server-side rendering is appropriate for performance
- Database session/transaction management, e.g. debugging Sqlalchemy session issues, the difference between flush and commit, and how to manage the connection pool
- Database query optimization and indexing strategies, ORM relationship mapping loading (Sqlalchemy join/select/selectin)
- RESTful API design principles and practical experience with authentication flows (OAuth, JWT) including token refresh and session security
- Caching strategies across the full stack - browser caching, CDN usage, Redis/Memcached patterns, and when to cache at different layers
- Production debugging skills using browser dev tools, server logs, and database query analysis to identify bottlenecks across the request lifecycle

## Senior Backend/Platform Engineer

- Common concurrency/async patterns, such as green threads, asyncio with async/await, what could block the executor, and when to choose each pattern based on I/O vs CPU-bound workloads
- Common parallelization techniques, such as Python thread/process pool/executors, and when process pools are necessary vs when threading suffices
- Python GIL, and how it exemplifies itself in various applications, web servers, job workers, how to architect applications to work around GIL limitations in web servers and job workers
- When to choose specific data formats (MessagePack for speed, Protobuf for schema evolution, Arrow for analytics, Parquet for storage) based on use case requirements
- How to saturate hardware resources and identify bottlenecks, such as CPU cores, disk IO, networking IO, and perform reliable benchmarks for client/server setups
- Load balancing strategies and when to scale horizontally vs vertically based on bottleneck analysis

## Senior Data & Systems Engineer

- Proficiency with systems languages (C/C++, Rust), and computing fundamentals. Knowledge of when to choose systems languages (C/C++, Rust) vs higher-level languages based on performance requirements and development velocity tradeoffs
- Strong experience with high-performance databases, e.g. RocksDB, LMDB, ScyllaDB, and mastery of common query patterns, such as point lookup and parallel iterator scans
- Strong familiarity with common data formats, e.g. MessagePack, Protobuf, Arrow, Parquet, etc., and when to choose one based on use case requirements
- Job queue architecture decisions: when to use Redis vs MQ vs Kafka based on nature of work, durability, throughput, and failure handling requirements
- Familiarity with the Python ecosystem: when to use NumPy, and when to use Pandas, Polars, etc.

## Senior ML Engineer (Computer Vision)

- Model architecture selection: when to use CNNs vs Vision Transformers vs hybrid approaches based on dataset size, computational constraints, and accuracy requirements
- Data preparation skills: how to store data at different stages of the ETL process, and how to use common approaches and libraries to dedupe & merge
- Training pipeline optimization: when to use mixed precision, gradient accumulation, and distributed training strategies based on hardware limitations and model size
- Deployment optimization: when to use model quantization, pruning, or knowledge distillation vs when to scale infrastructure, based on latency and throughput constraints
- Evaluation methodology: how to design proper train/validation/test splits for computer vision tasks and when standard metrics are insufficient for production requirements
- Production monitoring: how to detect model drift, data quality issues, and performance degradation in deployed CV systems, and when to trigger model retraining
- Hardware utilization: how to profile GPU memory usage, optimize batch sizes, and identify bottlenecks in data loading vs compute vs memory transfer
