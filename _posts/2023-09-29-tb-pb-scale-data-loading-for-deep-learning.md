---
layout: post
title: TB/PB-Scale Data Loading for Deep Learning
---

I've been looking into training some big datasets (500GBs ~ several TBs) of small images with PyTorch. Previously, I have been using a really old and inflexible, but quite efficient format, MXNet's [MXIndexedRecordIO](https://mxnet.apache.org/versions/1.7/api/python/docs/api/mxnet/recordio/index.html#mxnet.recordio.MXIndexedRecordIO). But there are more and more problems with it. As datasets get larger, it takes a long time to pull to disk from wherever the data is stored, and during distributed training, every rank has to have a copy on disk. Indexed random access sucks a lot of IOPs from disks too, so you would need good disks. It takes a lot of conditions to be met to actually start training.

The industry moved fast to find its own solutions. Tensorflow users would use [TFRecord](https://www.tensorflow.org/tutorials/load_data/tfrecord). There is [WebDataset](https://github.com/webdataset/webdataset), which is really just using tar files to store data in a certain way, and other libraries that support these formats. Essentially one would need to be able to stream the data, preferably in shards from the cloud, and train with window-shuffling as new chunks/shards are being downloaded.

Support for WebDataset has been slowly growing.

1. The [original](https://github.com/webdataset/webdataset) author's implementation is pretty good, but there are some [subtle areas](https://github.com/webdataset/webdataset/issues/250#issuecomment-1454094496) that might trip users. The documentation has outdated parts, interweaved with up-to-date parts. But if you work through them, it's a good solution.
2. [TorchData](https://pytorch.org/data/main/torchdata.datapipes.iter.html), a PyTorch affiliate has full support over it. However recently it [announced](https://github.com/pytorch/data/issues/1196) it had paused development because it needed to reevaluate the long-term vision.
3. [Ray Data]((https://docs.ray.io/en/latest/data/api/doc/ray.data.read_webdataset.html)) has an implementation and it was suggested to me during the recent Ray Summit. Although you would likely need to use the whole platform for it.
4. [NVIDIA DALI](https://docs.nvidia.com/deeplearning/dali/user-guide/docs/operations/nvidia.dali.fn.readers.webdataset.html#nvidia.dali.fn.readers.webdataset) supports the basic use of it, but apparently only loading from disk so far. One could however create an [external source](https://docs.nvidia.com/deeplearning/dali/user-guide/docs/examples/general/data_loading/parallel_external_source.html) in Python. The advantage of DALI is doing image transforms/augmentations on GPUs in CUDA streams, taking the load off CPUs. Although usually CPUs are sufficient at simple-ish augs.

I am currently switching between the original author's impl and the TorchData impl. They work reasonably well for my use case. The challenge has been handling interaction between distributed/multiprocessing and shard splitting. There are many GitHub issues around it, and the documentations are not written for users who *just want to shuffle and feed data correctly*. Essentially, in the WebDataset scheme, the data shards are treated as coarse indexes, and it requires some finessing to have all ranks receive the same number of batches to synchronize, and not lose some of the data.
These two libraries evolved with each other's influence, and made a lot of genius use of iterators and all kinds of iterator functions. It's kind of a nod to Rust's wide support for iterators.

Another solution for small files and images is [Parquet](https://www.databricks.com/glossary/what-is-parquet), which also has broad support. The challenge is it's such a flexible format, so one has to read within fine print to see what the library handles, and what you need to handle. Luckily, with data loading during training, the bottleneck is usually the GPU compute part, and even if ad-hoc custom plugins are slowish, it's still not a big problem.

Just jotting down notes in case others are wondering.
