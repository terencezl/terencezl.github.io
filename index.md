---
layout: default
title: Home
permalink: /
---
<img src="/public/imgs/terence4.jpg" class="img-circle"
     style="margin-left:auto;margin-right:auto;border-radius:50%;" width=200 height=200/>

-----------------

Well well. Welcome.

I am a leader in building and deploying **machine learning models**, **neural search engines**, and **parallel computing/data systems**. In 2021, I created a facial recognition [algorithm](https://pages.nist.gov/frvt/reportcards/11/clearviewai_000.html) that ranked **US #1** and **World #2** among top companies and research institutions. In 2022, I drove the research and implementation into a **deca-billion-scale** face search engine that was **100+** times the throughput of state-of-the-art, solving scalability once and for all. In achieving them, I designed multiple compact ML data pipelines and inference platforms. I also accumulated valuable experience & intuition on system abstraction, long-term maintainability, resource constraints, and efficiency maximizers.

As a highly motivated individual, I’m very hands-on with my work and believe in-depth experience and insights lead to strategic vision in this field. I find great potential to contribute at the intersection of research, engineering, and product. As a manager, I have led teams to excellence with fairness and empathy. I love being a team player and seek to understand established working patterns before instituting change. I make it a point to communicate and share knowledge that enriches and empowers my peers.

Here is some [media coverage](#media-highlights). I maintain a technical [Blog](/blog) and write occasionally. Please find me on [LinkedIn](https://www.linkedin.com/in/terence-z-liu/) if there are exciting opportunities ([CV](/public/cv.pdf)).

-----------------

## <u>EXPERIENCE</u>

Here allow me to delve a bit more into each experience than what's on a one-pager resume. I got this inspiration because we can so easily know about a company and its executives through interviews online on our own time, but the reverse is not true for individuals. This is a great place to do that.

### Clearview AI

_Head of ML / Principal Engineer, 2021 - Present_

I had previously worked on facial recognition back in 2017, and really wanted to solve the two biggest problems in the industry - the accuracy of the algorithm, and the accuracy & scalability of the face search engine at increasingly large sizes (deca-billion scale and more). Clearview was the perfect opportunity for me. I ended up solving them in each of the two years when I was here. In addition, I took on a lot more responsibilities, both in leadership/strategy and in people management.

* Created a facial recognition [algorithm](https://pages.nist.gov/frvt/reportcards/11/clearviewai_000.html) ranked **US #1** and **World #2**.
* Researched & implemented a **deca-B** vector database that was **100+** times the SOTA throughput. Fused high-profile open-source C++ libraries to push the industry boundary. Near-term 1/10 server cost & much higher capacity. Long-term $multi-M annual savings.
* Perfected efficient model training using tens of nodes/GPUs, enabling Research function.
* Drove model efficiency using distillation training, quantization, pruning & trimming, and hardware acceleration. Streamlined deployment with model encryption and serving engines.
* Led cross-functional collaboration to design & review multiple compact ML data pipelines & inference infra for images/videos, resulting in $100k cost reduction per recurring batch job.
* Established foundational ML practices, tooling & platform and built a team of ML engineers.
* Planned & executed product development & GTM of [PAD](https://www.biometricupdate.com/202208/clearview-reveals-biometric-presentation-attack-detection-feature-talks-training-and-testing) feature with team.
* Co-wrote marketing materials and public letters. Engaged with policy officials.

I encountered a vast lineup of technologies along the way, and became a proficient user in order to get the most out of them. They ranged from ML frameworks **PyTorch**, **OpenCV**, **ONNX Runtime**, **OpenVINO**, **CuPy**, **TensorRT**, powerful MLOps platforms/tools **AWS SageMaker**, **GCP Vertex AI**, [**Ray**](https://github.com/ray-project/ray), **Airflow**, **Flyte**, **MLFlow**, **DVC**, approximate nearest neighbors libraries [**Faiss**](https://github.com/facebookresearch/faiss/), [**hnswlib**](https://github.com/nmslib/hnswlib), and general SWE tools **FastAPI**, **Socket.IO**, **Protobuf & gRPC**, **Redis Stream**, [**RocksDB**](https://github.com/facebook/rocksdb), **Datadog**, **GitLab CI/CD**, **Docker**, **Kubernetes**. I had to take face detectors and embedders apart in pieces and put them back together with different acceleration framework backends to understand how to create the best interfaces. I fused three tough C++ libraries (and more utility ones) together to arrive at what I needed for things to scale. They were incredibly challenging and equally fun.

<details markdown=block>
<summary markdown=span>**MORE**</summary>

> During this time I got to be the sole person pushing through from data collection, pipelining, cleaning, preprocessing, training & experimentation, model productionization/inference optimization, all the way to indexing for search at a very large scale. These tasks encompassed almost the entirety of the industrial ML/DL specializations.
>
> My role here was a combination of _ML Research Scientist/Engineer_ and _ML Platform Engineer_. The latter one echoed back with my experience at [Bloomberg](#bloomberg-lp) doing platform work. In addition, due to the visual nature of computer vision, being able to anticipate and connect to the frontend/product experience was essential. Therefore I took lead roles at adjacent teams and contributed heavy-handedly to a few projects. The aim was to drive the initiatives to the logical conclusions and reap the benefits of what the ML core had to offer. Through them I got to really stretch my abilities. The hands-on technical experience and intuition I gained from these projects were priceless.
>
> * One project was a rewrite of the MLAPI service with the GPU batching engine **service streamer** that was simple, flexible and effective. - It was like [Ray Serve](https://www.ray.io/ray-serve).
> * Another project was a distributed ML data pipeline framework that was fault tolerant for spot GPU instances, orchestrated minimally by S3, Redis, `rsync`, `ssh` and UNIX tools. It was flexible for reuse and enabled observability by terminal dashboards (`tmux`, `watch`).
> * Another project was a multithreaded video frame ML processor that parsed unique face groups with tracking and clustering.
> * Another project was re-architecting the neural vector DB/index engine, which ended up being **5** times more efficient, then another **100+** times on top of that, solving scalability once and for all.
>
> I also carried various projects from research & prototyping to production in accelerated time frames, and obtained very concrete rules to determine progress in a sea of complexity. I defined the Technology Process in the context of the company: problem definition & claim, strategizing & planning, solving & characterization, and production implementation stages. I made sure to communicate the expectations and stop gaps at each stage. With a few projects completed, I demonstrated that technology leadership could be driven out of a persistent vision.
>
> Since the algorithm's debut success, I became the trusted expert on the core tech in the leadership team and took on the scientific authority in product marketing and policy & legal messaging. I built the Research/ML division, laid out the technological foundation and assembled a team. I was very keen on nurturing the team, sharing knowledge, and recording sessions for broader access & history keeping, a practice I picked up during the pandemic remote working environment. Recently I came across a book [The Staff Engineer's Path](https://newsletter.pragmaticengineer.com/p/the-staff-engineers-path) (highly recommend!) and found a lot of common themes.
</details>

-----------------

### Bloomberg LP

_Senior Software Engineer, Platform, 2017 - 2021_

I moved into the industry and realized I really liked to work with computers in a more general capacity. In order to take things to the next level, I needed more rigorous training in Software Engineering. Here I became a more equipped developer, and learned on the job key data structures, system design patterns, essential tools and frameworks.

* Maintained & monitored widely-used bare-metal SFTP infrastructure with 7M daily logins.
* Designed & implemented reliable account management, auth, routing, caching, messaging for cloud-based next-gen SFTP. Wrote OS-level modules and web servers for auth interfacing with OpenSSH. Managed deployment on internal Kubernetes-based PaaS.
* Leveraged S3 Storage as SFTP subsystem with file system emulation and cross-data-center replication & failover.
* Spearheaded successful multi-year high-stake account migration as technical lead.

At Bloomberg I became serious with **C++** (it's a C++ shop after all!), **Golang**, **OpenSSH**, Web development stack **Flask**, **SQLAlchemy**, **Postgres**, **Redis**, **MongoDB**, data/messaging frameworks **RabbitMQ**, **Kafka**, **Flink**, **Spark**, system monitoring tools **Grafana**, **Splunk**, **Humio**, DevOps & Platform Engineering tools **Jenkins**, **Chef**, **Docker**, **Kubernetes**, **OpenStack**. I took a special interest in scalable data/messaging pipeline and database components. Meanwhile I kept learning about ML/AI on the side.

<details markdown=block>
<summary markdown=span>**MORE**</summary>
> The work here felt like a high-stake crash course of the book [System Design Interview](https://www.amazon.com/System-Design-Interview-insiders-Second/dp/B08CMF2CQF). Clients, servers, DNS, API gateways, load balancers, proxies, route hosts, databases, caches, message buses, logging, metrics, rate limting, JWT auth, cryptographic padding/cert signing, user models, isolated networks and staged rollouts... and a lot more. It was humbling to see it first hand how seasoned engineers deal with large systems serving millions of users and requests every day. I made valuable contributions to the over-arching theme of transitioning from the old system to the new system, and matured into the likes of my peers.
</details>

-----------------

### University of Toledo

_Ph.D., Physics, 2012 – 2017_<br>
_Researcher & Developer, 2013 - 2017_

I spent four of the five years here as a funded researcher working on First-Principles materials simulations with [Density Functional Theory](https://en.wikipedia.org/wiki/Density_functional_theory) on supercomputing clusters. It was an exciting field that only became feasible after ~50 years of advances in supercomputing since WWII... not just quantum mechanics theories anymore. However the tooling around the core Fortran software package [VASP](https://www.vasp.at/) was very scarce, and I had to be very proactive about what to learn and build. This journey taught me a lot of things, _resilience_ being the most valuable aspect of it. Because of the fundamental similarity in problem scope (iterative optimization), working approach (scientific experiments) and technical requirements (big computers), it naturally paved my way to the growing Data Science and Machine Learning fields, and as soon as GPUs became more available, Deep Learning.

* Specialized in materials simulations with parallel computing clusters. 14 [papers](https://scholar.google.com/citations?user=AT89GwYAAAAJ&hl=en) published.
* Calculated electronic ground states with gradient descent & residual minimization schemes, (non-)linear regression - similar routines as in ML/DL frameworks. Had various classical ML [projects](/projects/).
* Authored open-source projects: [ScriptsForVASP](https://github.com/terencezl/ScriptsForVASP), [pydass_vasp](https://github.com/terencezl/ScriptsForVASP), [pyvasp-workflow](https://github.com/terencezl/pyvasp-workflow).
* Built a materials database [website](/projects/#ceramics-database) with a modern stack, supporting tabulation/graphing, user auth/contribution. Project helped get a $100k research grant.
* Mentored three undergraduate and two graduate students.

Here I became proficient with **Linux** and **Python** and their **scientific computing** eco-systems, e.g. **NumPy**, **SciPy**, **scikit-learn**, **XGBoost**, **LightGBM**, **pandas**, **matplotlib**, etc. I took a lot of additional courses and did [projects](/projects/) to be fully equipped in SWE/ML/DL in the industry.

<details markdown=block>
<summary markdown=span>**MORE**</summary>

> Additional courses:
>
> * Statistical Inference (MATH 8650)
> * Categorical Data Analysis (MATH 8620)
> * Topics In Statistics (MATH 8640)
> * Statistical Consulting (MATH 8600)
>
> Online courses:
>
> * Introduction to Databases (Stanford) - with Distinction
> * Algorithms, Part I (Princeton)
> * Introduction to Probability and Data (Duke)
> * Inferential Statistics (Duke)
> * R Programming (Johns Hopkins)
> * Regression Models (Johns Hopkins)
> * Practical Machine Learning (Johns Hopkins)
> * Statistical Learning “ISLR” (Stanford)
>
> [Dissertation on material properties prediction with cluster expansion regression models](http://iopscience.iop.org/article/10.1088/0953-8984/29/3/035401)
>
> > Predicting properties from atomic configurations with linear models, cross validation and selection (cluster expansion formalism).
>
> ![img](/public/imgs/TiN.jpg){: style="width: 90%;max-width:600px" }
>
> NOTE: if you would like to plan for a transition from PhD to the SWE/ML/AI industry, prepare early, and read [A Survival Guide to a PhD](http://karpathy.github.io/2016/09/07/phd/) from Andrej Karpathy and the [HN discussion](https://news.ycombinator.com/item?id=12447495).
</details>

-----------------

### Nanjing University

_Bachelor of Science, Materials Science & Engineering, 2008 – 2012_

This major was interdisciplinary in nature. As a result, I studied a broad range of subjects: materials science & engineering, physics, chemistry, electrical engineering, computer science, math, statistics, etc. I also prepared and participated in a mathematical modeling contest with a team that focused on operations research using **MATLAB** and **Mathematica**.

-----------------

## <u>MEDIA HIGHLIGHTS</u>

[NYT: Clearview AI finally takes part in a federal accuracy test.](https://www.nytimes.com/2021/10/28/technology/clearview-ai-test.html)

_(2021-10-28)_

> In a field of over 300 algorithms from over 200 facial recognition vendors, Clearview ranked among the top 10 in terms of accuracy, alongside NTechLab of Russia, Sensetime of China and other more established outfits.

-----------------

[NYT: Clearview AI does well in another round of facial recognition accuracy tests.](https://www.nytimes.com/2021/11/23/technology/clearview-ai-facial-recognition-accuracy.html)

_(2021-11-23)_

> In results announced on Monday, Clearview, which is based in New York, placed among the top 10 out of nearly 100 facial recognition vendors in a federal test intended to reveal which tools are best at finding the right face while looking through photos of millions of people.

-----------------

[Reuters: EXCLUSIVE Facial recognition company Clearview AI seeks first big deals, discloses research chief](https://www.reuters.com/technology/exclusive-facial-recognition-company-clearview-ai-seeks-first-big-deals-2022-02-22/)

_(2022-02-22)_

> Ton-That said **Terence Liu** is the Pennsylvania-based computational physicist behind some of Clearview's algorithms and its vice president of research. They are listed together on a patent application filed Tuesday… The research head Liu formally joined last year after working as a senior software engineer at Bloomberg LP since 2017, he said. He earlier had partnered with Ton-That to advance Clearview's prototype.

-----------------

[Biometric Update: Clearview reveals biometric presentation attack detection feature, talks training and testing](https://www.biometricupdate.com/202208/clearview-reveals-biometric-presentation-attack-detection-feature-talks-training-and-testing)

_(2022-08-10)_

> Clearview’s technology focuses on single images from commercial RGB images, VP of Research **Terence Liu** told Biometric Update during the same video call… Clearview takes an ensemble approach, combining models that look for different things, Liu says.

<iframe title="vimeo-player" src="https://player.vimeo.com/video/737559530?h=be84cede9f" width="95%" height="300" frameborder="0" allowfullscreen></iframe>

-----------------

[Biometric Update: Clearview patent on method for scaling biometric training dataset gets US notice of allowance](https://www.biometricupdate.com/202208/clearview-patent-on-method-for-scaling-biometric-training-dataset-gets-us-notice-of-allowance)

_(2022-08-25)_

> Clearview Vice President of Research **Terence Liu** explained to Biometric Update in an interview that face biometrics algorithms are trained by ingesting several images from each subject, and then organizing data from ingested images into “clusters” with other images from the same subject.
