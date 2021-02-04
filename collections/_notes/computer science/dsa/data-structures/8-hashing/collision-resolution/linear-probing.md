---
layout: post
title: Linear probing
permalink: /ds/hashing/linear-probing
---

- interval between probes is fixed at 1.
- we search the hash table sequentially,starting from the original hash location.
  - If a location is occupied, we check the next location.
  - We wrap around from the last table location to the first table location if necessary. 
- `rehash(key) = (n+1)%tableSize`
- table contains groups of consecutively occupied locations that are called clustering. 
  - one part of the table might be quite dense, even though another part has relatively few items.
- The step-size should be relatively prime to the table size.
  - If we choose the table size to be a prime number, then any step-size is relatively prime to the table size.
  - Clustering cannot be avoided by larger step-sizes.
