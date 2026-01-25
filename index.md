---
layout: default
title: Home
permalink: /
---
<img src="/public/imgs/terence4.jpg" class="img-circle"
     style="margin-left:auto;margin-right:auto;border-radius:50%;" width=200 height=200/>

-----------------

I build **machine learning models**, **vector search engines**, and **large-scale data systems**. With a background in computational physics, I am interested in performance computing and the hardware, language, and software advances that shape systems at scale.

I work closely with production systems and teams, focusing on changes that improve outcomes. I aim to understand how systems are actually used before evolving them, so performance and simplicity compound rather than fight the organization.

In this [blog](/blog), I write about the technical and the organizational, where implementation meets strategy. Early in my career, I optimized for performance. Now I optimize for decisions.

-----------------

## <u>EXPERIENCE</u>

### Clearview AI

_Interim Head of Engineering, 2025_<br>
_Head of ML / Principal Engineer, 2021 - 2025_

I had previously worked on computer vision / facial recognition back in 2017, and really wanted to solve the two biggest problems in the industry - the accuracy of the algorithm, and the accuracy & scalability of the vector search engine at increasingly large sizes (deca-billion scale and more). I ended up solving them in the first two years. Further, I grew a lot more, both into technical systems engineering and scaling engineering goals & operations.

* Created a facial recognition [algorithm](https://pages.nist.gov/frvt/reportcards/11/clearviewai_000.html) ranked **US #1** and **World #2** (time of submission) by [NIST](https://pages.nist.gov/frvt/html/frvt11.html) ([updated](https://face.nist.gov/frte/reportcards/11/clearviewai_002.html) in 2024).
* Researched & implemented a **deca-B** [vector search engine](https://www.clearview.ai/post/how-we-store-and-search-30-billion-faces) that has proven its value. Fused high-profile open-source C++ libraries and created Python bindings. $MM annual savings.
* Achieved SOTA accuracy in the domain category with efficient model training orchestrating a cluster of nodes. Became early adopters of alternative chips, e.g. [Intel Habana Gaudi2](https://habana.ai/products/gaudi2/).
* Drove model efficiency using distillation training, quantization, pruning/trimming & hardware acceleration. Streamlined deployment with model encryption & serving engines. Early user of the NVIDIA stack - [TensorRT](https://developer.nvidia.com/tensorrt)/[Triton](https://developer.nvidia.com/dynamo-triton).
* Established foundational ML/data practices & native (C++ & Rust) tooling for performance-sensitive tasks.
* Designed & implemented multiple compute-intensive data pipelines & inference infra for images/videos, resulting in $100k cost reduction per recurring batch job.
* Consolidated infra and renegotiated with vendors, leading to **40% drop** of infra COGS.
* Revamped team processes and executed on hiring of key divisions.
* OSS work: [msgpack-numpy-rs](https://github.com/clearviewai/msgpack-numpy-rs), [sulfite](https://github.com/clearviewai/sulfite)

-----------------

### Bloomberg LP

_Senior Software Engineer, Platform, 2017 - 2021_

I became more equipped with key data structures, system design patterns, essential tools, and frameworks.

* Maintained & monitored widely-used bare-metal SFTP infra with 7M daily logins.
* Designed & implemented reliable account management, auth, routing, caching, messaging for cloud-based next-gen SFTP. Wrote OS-level modules and web servers for auth interfacing with OpenSSH. Managed deployment on internal Kubernetes-based PaaS.
* Leveraged S3 Storage as SFTP subsystem with file system emulation and cross-data-center replication & failover.
* Spearheaded successful multi-year high-stake account migration as technical lead.

-----------------

### University of Toledo

_Ph.D., Physics, 2012 – 2017_

I spent four of the five years here as a funded researcher working on First-Principles materials simulations with [Density Functional Theory](https://en.wikipedia.org/wiki/Density_functional_theory) on supercomputing clusters. It was an exciting field that only became feasible after ~50 years of advances in supercomputing since WWII... not just quantum mechanics theories anymore. However the tooling around the core Fortran software package [VASP](https://www.vasp.at/) was very scarce, and I had to be very proactive about what to learn and build. This journey taught me a lot of things, _resilience_ being the most valuable aspect of it. Because of the fundamental similarity in problem scope (iterative optimization), working approach (scientific experiments) and technical requirements (big computers), it naturally paved my way to the growing Data Science and Machine Learning fields, and as soon as GPUs became more available, Deep Learning.

* Specialized in materials simulations with parallel computing clusters ([papers](https://scholar.google.com/citations?user=AT89GwYAAAAJ&hl=en)).
* Calculated electronic ground states with gradient descent & residual minimization schemes, (non-)linear regression - similar routines as in ML/DL frameworks. Had various classical ML projects.
* Authored open-source projects: [ScriptsForVASP](https://github.com/terencezl/ScriptsForVASP), [pydass_vasp](https://github.com/terencezl/ScriptsForVASP), [pyvasp-workflow](https://github.com/terencezl/pyvasp-workflow).
* Built a materials database website with a modern stack, supporting tabulation/graphing, user auth/contribution.

<details markdown=block>
<summary markdown=span>**Dissertation**</summary>

> [Dissertation on material properties prediction with cluster expansion regression models](http://iopscience.iop.org/article/10.1088/0953-8984/29/3/035401)
>
> Predicting properties from atomic configurations with linear models, cross validation and selection (cluster expansion formalism).
>
> ![img](/public/imgs/TiN.jpg){: style="width: 90%;max-width:600px" }
>
> NOTE: if you would like to plan for a transition from PhD to the SWE/ML/AI industry, prepare early, and read [A Survival Guide to a PhD](http://karpathy.github.io/2016/09/07/phd/) from Andrej Karpathy and the [HN discussion](https://news.ycombinator.com/item?id=12447495).
</details>

-----------------

### Nanjing University

_Bachelor of Science, Materials Science & Engineering, 2008 – 2012_

This major was interdisciplinary in nature. As a result, I studied a broad range of subjects: materials science & engineering, physics, chemistry, electrical engineering, computer science, math, statistics, etc. I also prepared and participated in a mathematical modeling contest with a team that focused on operations research.

-----------------

## <u>TALKS</u>

[Migrating 50TB Data From a Home-Grown Database to ScyllaDB, Fast](blog/2025/03/04/migrating-50tb-to-scylladb-fast/)

_(2025-03-04)_

<div style="max-width: 95%; width: 305px; height: 190px;">
<iframe width="100%" height="100%" src="https://www.youtube.com/embed/q1GZEwLKTug?si=FeHFTFhgABIcWwMS" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</div>

> Terence shares how Clearview AI's infra needs evolved and why they chose ScyllaDB after first-principles research. From fast ingestion to production queries. The talk explores their journey with embedded DB readers and the ScyllaDB Rust driver, plus config tips for bulk ingestion and achieving data parity.

[The Rust Invasion: New Possibilities in the Python Ecosystem](/blog/2024/10/10/the-rust-invasion/)

_(2024-10-10)_

<div style="max-width: 95%; width: 305px; height: 190px;">
<iframe src="https://docs.google.com/presentation/d/e/2PACX-1vTPcjPJfL0o0XdVozmhDLsKN88OG-LNPmFvWmy91ZUqsGMmMCb1moCer5uIc0ZOTMPU6WFX6AbfgJHr/embed?start=false&loop=false&delayms=3000" frameborder="0" width="100%" height="100%" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe>
</div>

> I presented at the local [MadPy](https://madpy.com/meetups/2024/10/10/20241010-the-rust-invasion/) meetup group on the new possibilities in the Python ecosystem in light of recent development in the Rust world. Spent some time curating those links, so they may be worth a shuffle!

-----------------

## <u>MEDIA</u>

[Interview with Biometric Update: How Clearview developed its method for fast search on an above-billion scale database](https://www.biometricupdate.com/202306/how-clearview-developed-its-method-for-fast-search-on-an-above-billion-scale-database)

_(2023-06-28)_

> As explained in a company blog post by Liu and expanded on in conversation with Biometric Update, Clearview believes the smarter way is to index vectors so only small portion needs to be searched. This means “you can effectively search only a small portion of the database, finding very highly likely matches,” Liu says.

[Blog Post: How We Store and Search 30 Billion Faces](https://www.clearview.ai/post/how-we-store-and-search-30-billion-faces)

_(2023-04-18)_

> The Clearview AI platform has evolved significantly over the past few years, with our database growing from a few million face images to an astounding 30 billion today. Faces can be represented and compared as embedding vectors, but face vectors have unique properties that make it challenging to search at scale.

-----------------

[Interview with Biometric Update: Clearview patent on method for scaling biometric training dataset gets US notice of allowance](https://www.biometricupdate.com/202208/clearview-patent-on-method-for-scaling-biometric-training-dataset-gets-us-notice-of-allowance)

_(2022-08-25)_

> Clearview Vice President of Research Terence Liu explained to Biometric Update in an interview that face biometrics algorithms are trained by ingesting several images from each subject, and then organizing data from ingested images into “clusters” with other images from the same subject.

-----------------

[NYT: Clearview AI does well in another round of facial recognition accuracy tests.](https://www.nytimes.com/2021/11/23/technology/clearview-ai-facial-recognition-accuracy.html)

_(2021-11-23)_

> In results announced on Monday, Clearview, which is based in New York, placed among the top 10 out of nearly 100 facial recognition vendors in a federal test intended to reveal which tools are best at finding the right face while looking through photos of millions of people.

-----------------

[NYT: Clearview AI finally takes part in a federal accuracy test.](https://www.nytimes.com/2021/10/28/technology/clearview-ai-test.html)

_(2021-10-28)_

> In a field of over 300 algorithms from over 200 facial recognition vendors, Clearview ranked among the top 10 in terms of accuracy, alongside NTechLab of Russia, Sensetime of China and other more established outfits.
