---
layout: page
title: Projects
permalink: /projects/
---

## Rust Crates

## [sulfite](https://github.com/clearviewai/sulfite)

> `sulfite` is a high-level S3 client built on [AWS SDK for Rust](https://awslabs.github.io/aws-sdk-rust/) for even better ease of use, reliability, and bandwidth saturation (>50 Gbps).
> The name: `SO3^2-`, an anion, implying a companion to some other cation (application), is commonly used as a preservative in wines and dried fruits (preserve to S3). It's `S3` with an `O` in the middle, a play on [oxidization](https://wiki.mozilla.org/Oxidation).

-----------------

## [msgpack-numpy-rs](https://github.com/clearviewai/msgpack-numpy-rs)

> This crate does what Python's [msgpack-numpy](https://github.com/lebedov/msgpack-numpy/) does in Rust, and a lot [faster](https://github.com/clearviewai/msgpack-numpy-rs?tab=readme-ov-file#benchmarks). It serializes and deserializes NumPy scalars and arrays to and from the [MessagePack](https://msgpack.org/) format, in the same serialized formats as the Python counterpart, so they could interoperate with each other. It enables processing NumPy arrays in a different service in Rust through IPC, or saving Machine Learning results to disk (better paired with compression).
