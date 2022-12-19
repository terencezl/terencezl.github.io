---
layout: post
title: Thoughts on ML Research
---

Not every business needs a Research function, certainly not every startup. However if a startup’s bread and butter is advanced technology, a sustained effort has to be put into maintaining it and cutting out new paths. The Research function’s role is to tease and trek into the unknown, to distill the craft into our potential area of expertise. In fulfilling this function, it needs to be comfortable not knowing how the piece of technology exactly fits into the product timeline and coordination - if we are confident in specing out even the big strokes at the beginning, it’s not research but engineering execution. Instead, it needs to do the following things.

1. It needs to identify and appreciate a big challenge, take comfort and joy in the craft itself, and recognize the fact that the problem is meaningful enough that any findings coming out of it could shape key directions for the business.
2. It needs to formulate hypotheses, set up environments to prove or disprove them quickly in the most representative yet still efficient way, and change course quickly in a matter of days and weeks. The code written and tools built during the many fail-fast attempts do not get thrown away, but factored into common elements and components in a broad collection of Swiss army knives that can be repurposed easily.
3. It needs to be fixated on the important details, retain a long working memory, turn every stone and record them, and aim to incrementally become an expert on the subject.
4. It needs to identify milestones particular to the different branching points, systematically approach them in overlapping time frames, and have the will to drive through to the conclusion.

Perhaps the biggest realization is that it is a constant battle against the unlikely, the seemingly impossible, a race against stasis and inertia. You have to move quickly enough to not let the problem drag you down and by working incredibly resiliently, you start to create a rhythm. Once you have a rhythm you know what you can tackle, and this internal knowledge and comfort gauge can go a very long way. In particular, big computers will be your best friend, and wielding a huge amount of computing resources will put new power and responsibility onto your hands. You’ll plan around off hours trying to fill in jobs that run overnight, and still maintain the pace of the project during the 2/3 of the day not on business hours. I’ve observed this habit up to Big Tech companies’ ML Research function, so it’s not something only frugal startups do. It’s the natural rhythm of work in this field.

In this light, research practitioners need to be able to independently carry out scientific experiments, but also need to be excellent low-level engineers, who understand algorithms, primitives, time complexity, various hardware constraints (compute, memory, networking IO, disk IO), and are handy with a few languages that are close to hardware. In our line of business, they need to be good at parallel programming with CPUs and GPUs to be proficient at wielding large-scale datasets. They need to approach tools from First-Principles “what exactly do I want to do, and how does this tool uniquely help me get there when I can’t do it myself”, instead of adopting some opaque established system that people say is good.

There is a distinction between ML Engineering work and Research work, despite sharing a lot of knowledge and assets in common. These are relevant research topic examples. They all involve dealing with a substantial amount of unknowns, and outcomes that inherently will become premium features to the core product instead of “we also have it” that are 90% good. It’s “best or bust”. If we do a good job, customers will choose no one but us, and we can be ahead of competitors by a good margin, and we get to shape the next step.

1. Algorithms that demonstrate extremely low error rates and bias
2. Models that require extensive large-scale parallel cleaning, training and testing.
3. Model acceleration/quantization with speed and accuracy tradeoffs
4. Applications that need to be fast at every step for real-time use
5. Applications that need to be vastly scalable that cannot be easily addressed by duplicating servers

These are problems more suited in Engineering, broadly MLOps.

1. ML model accessor design, code base organization, CI/CD pipelines, package integration, model artifacts, Docker image management
2. ML model serving engine with different formats catering to different use cases (latency vs throughput), batching, GPU resource management (slicing/timeshare)
3. ML-centric pipelines, components for data ingestion, user upload processing and delivery
4. Orchestration of various ML models, algorithms together for a business function, exposure to Web endpoint for API user or front-end consumption
5. Custom labeling services, online training & labeling pipelines

The MLOps function as an Engineering unit serves the rest of Engineering/Product and in addition, Research. Cases #1, #2, #3 target the shared infra, #4 for Engineering/Product, and #5 for Research.

It has become clear to me the ML Engineering work and Research work require different types of people. It requires years to train them to be who they are not. When one provisions people to fill the Research function, s/he needs to realize they excel by depth, not “speed to a prototype”. S/he needs to think about the business assuming certain research projects are a reality, and how it could greatly benefit the business, and commit backwards to guide the hiring plan. It needs to be the right people, the right specialists. It is extremely hard to motivate people to do deep research except when it is a topic the person is really into, has great relevant experience and preparation for, and is given an abundant amount of ownership, trust and resources to tackle. But, if you get it right, you get magic in return.
