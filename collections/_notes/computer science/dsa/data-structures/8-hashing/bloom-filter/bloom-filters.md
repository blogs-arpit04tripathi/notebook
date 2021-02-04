---
layout: post
title: Bloom Filters
permalink: /:collection/cs/ds/hashing/bloom-filters
---

- A probabilistic data structure which was designed to check whether an element is present in a set with memory and time efficiency.
- It tells us that the element either
  - definitely is not in the set, or
  - may be in the set.
- The base data structure of a Bloom filter is a Bit Vector.
- The algorithm relies on the use of a number of different hash functions.

**How it works?**

- apply k different hash functions to set bits.
- Search
  - apply the k hash functions and look up the indicated array elements.
    - If any of them are 0 we can be 100% sure that we have never encountered the element before.
    - Even if all of them are one, we still can’t conclude that we have seen the element.
      - All of the bits could have been set by the k hash functions applied to multiple other elements.
      - All we can conclude is that it is likely that we have encountered the element before.
- ***It is not possible to remove an element from a Bloom filter.***
  - We can’t unset a bit that appears to belong to an element because it might also be set by another element.
- If the bit array is mostly empty, i.e., set to zero, and the k hash functions are independent of one another, then the probability of a false positive is low.
  - As the bit array fills up, the probability of a false positive slowly increases.
- **One-time removal of an element from a Bloom filter can be simulated by having a second Bloom filter that contains elements that have been removed.**
  - false positives in the second filter become false negatives in the composite filter, which may be undesirable.
  - In this approach, readding a previously removed item is not possible, as one would have to remove it from the removed filter.

![](https://github.com/arpit04tripathi/files-cdn/raw/cdn/dsa/ds/hashing/bloom-filters.png)

**Selecting hash functions**
- k different independent hash functions.
- For a good hash function with a wide output, there should be little if any correlation between different bit-fields of such a hash, so this type of hash can be used to generate multiple different hash functions by slicing its output into multiple bit fields. 
- Alternatively, one can pass k different initial values (such as 0, 1, ..., k - 1) to a hash function that takes an initial value - or add (or append) these values to the key.

**Selecting size of bit vector**
- A Bloom filter with **1% error** and an optimal value of k, in contrast, requires only about **9.6 bits per element** – regardless of the size of the elements. 
- The 1% false positive rate can be reduced by a factor of ten by adding only about 4.8 bits per element.

**Space Advantages**
- Bloom filters have a strong space advantage over other data structures for representing sets, such as self-balancing binary search trees, tries, hash tables, or simple arrays or linked lists of the entries.
- No elements, no pointers here.

**Time Advantages**
-  The time needed either to add items or to check whether an item is in the set is a fixed constant, O(k), completely independent of the number of items already in the set.
-  Average access time of sparse hash tables can make them faster in practice than some Bloom filters.
   -  In a hardware implementation, however, the Bloom filter shines because its k lookups are independent and can be parallelized.
