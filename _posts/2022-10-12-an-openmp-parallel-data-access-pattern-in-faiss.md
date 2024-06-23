---
layout: post
title: An openmp Parallel Data Access Pattern in Faiss
---

This is a quick note on how to use `openmp` or rather, any multithreading library to divide the underlying data. Let's use some code snippets from Faiss.

Usually you would `parallel for`, or first `parallel` then `for` over a sequence. For [example](https://github.com/facebookresearch/faiss/blob/v1.7.2/faiss/IndexIVF.cpp#L350):

```c++
        int nt = std::min(omp_get_max_threads(), int(n));

#pragma omp parallel for if (nt > 1)
        for (idx_t slice = 0; slice < nt; slice++) {
            IndexIVFStats local_stats;
            idx_t i0 = n * slice / nt;
            idx_t i1 = n * (slice + 1) / nt;
```

I came across a different [use case](https://github.com/facebookresearch/faiss/blob/v1.7.2/faiss/IndexIVF.cpp#L253) that was note-worthy:

<!--more-->

```c++
    DirectMapAdd dm_adder(direct_map, n, xids);

#pragma omp parallel reduction(+ : nadd)
    {
        int nt = omp_get_num_threads();
        int rank = omp_get_thread_num();

        // each thread takes care of a subset of lists
        for (size_t i = 0; i < n; i++) {
            idx_t list_no = coarse_idx[i];
            if (list_no >= 0 && list_no % nt == rank) {
                idx_t id = xids ? xids[i] : ntotal + i;
                size_t ofs = invlists->add_entry(
                        list_no, id, flat_codes.get() + i * code_size);

                dm_adder.add(i, list_no, ofs);

                nadd++;
            } else if (rank == 0 && list_no == -1) {
                dm_adder.add(i, -1, 0);
            }
        }
    }
```

Here you just use `parallel` but not `for`. Instead, you get the total N of threads `nt`, and thread rank/number `rank`. Every single thread enters the entire `for` loop, iterating over each element. However, there is a conditional, which guarantees each element is processed at most once by one thread alone. Here it is done by the modulo `list_no % nt`. This allows all elements that are identified by a unique `list_no` to be exclusively handled by one thread, serially without possible race conditions. The beauty of it is that you get to accumulate states for each element's turn without ever needing a lock on the accumulator (the one that is identified by `list_no` in this case). It is very efficient for similar scenarios.

I also happened to encounter this pattern in a [write-up](https://greg7mdp.github.io/parallel-hashmap/). Check out the _Using the intrinsic parallelism of the `parallel_flat_hash_map` to insert values from multiple threads, lock free_ section. BTW, you NEED to check out [parallel-hashmap](https://github.com/greg7mdp/parallel-hashmap).
