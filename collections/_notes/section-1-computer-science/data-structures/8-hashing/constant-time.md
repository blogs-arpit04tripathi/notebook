---
layout: post
title: How Hashing gets O(1) Complexity
permalink: /:collection/cs/ds/hashing/constant-time
---

**how hashing gets O(1) if multiple elements map to the same location?**
- By using the load factor we make sure that each block (for example, linked list in separate chaining approach) on the average stores the maximum number of elements less than the load factor.
  - In practice this load factor is a constant (generally, 10 or 20).
  - As a result, searching in 20 elements or 10 elements becomes constant.
- If the average number of elements in a block is greater than the load factor, we rehash the elements with a bigger hash table size.
- The access time of the table depends on the load factor which in turn depends on the hash function.
- we generally use hash tables in cases where searches are more than insertion and deletion operations.
