---
layout: post
title: Little-Endian Snafu
---

You learned about this in college classes. You thought working SWE jobs in 2022 you'd never have to deal with this. But it comes back to trick you at your worst.

I was tripped by endian-ness when implementing inverted list [`listno-offset`/`LO`](https://github.com/facebookresearch/faiss/blob/v1.7.2/faiss/invlists/DirectMap.h#L21-L31) as a fixed-width binary key in RocksDB.

```c++
// When offsets list id + offset are encoded in an uint64
// we call this LO = list-offset

inline uint64_t lo_build(uint64_t list_id, uint64_t offset) {
    return list_id << 32 | offset;
}

inline uint64_t lo_listno(uint64_t lo) {
    return lo >> 32;
}

inline uint64_t lo_offset(uint64_t lo) {
    return lo & 0xffffffff;
}
```

<!--more-->

The original implementation used rather smart bitwise shifting and masking to accommodate two `uint32` integers in `uint64` allocations into one `uint64` integer. It worked out beautifully on its own. I proceeded to set up my custom [comparator](https://github.com/facebook/rocksdb/wiki/Basic-Operations#comparators) in RocksDB reinterpreting the `uint64` integer `LO` as a byte string, and that worked out great. Then I discovered [_prefix seek_](https://github.com/facebook/rocksdb/wiki/Prefix-Seek) and slapped on a `NewFixedPrefixTransform(4)` (4 bytes for the `list_id`/`listno`). This was when the iterator seeks broke down. One should expect all elements prefixed by the same `listno` to be returned with the fixed prefix, but the results suggested otherwise. It somehow seemed to be treating the `offset` as the prefix.

I spent hours isolating the problem with trial and error. Then at dinner it dawned on me... **Little Endian**[^1][^2]!

> When memory bytes are printed sequentially from left to right (e.g. in a hex dump), little-endian representation of integers has the significance increasing from left to right. In other words, it appears backwards when visualized, which can be counter-intuitive.

A (most?) modern `x86_64` or `aarch64` machine adopts a little-endian system. Here, a naive slice of the first 4 bytes in that memory blob would give you the `offset`, not the `listno`!

Realizing that, the fix was to build `LO` with string concatenation or `memcpy` in the expected order. And the problem was solved.

------
[^1]: https://en.wikipedia.org/wiki/Endianness
[^2]: https://chortle.ccsu.edu/assemblytutorial/Chapter-15/ass15_3.html
