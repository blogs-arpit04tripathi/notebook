---
layout: post
title: TreeMap
permalink: /:collection/java/collections/treemap
---

* It creates maps stored in a tree structure. 
* TreeMap stores key/value pairs in sorted order with rapid retrieval. 
* The fourth form initializes a tree map with the entries from sm, which will be sorted in the same order as sm.

```java
TreeMap( )
TreeMap(Comparator<? super K> comp)
TreeMap(Map<? extends K, ? extends V> m)
TreeMap(SortedMap<K, ? extends V> sm)
```

* Treemap is sorted according to the natural ordering of its keys, or by a Comparator provided at map creation time, depending on which constructor is used.
* ***log(n) time for containsKey(), get(), put() and remove().***
* Fail-Fast iterator.
* clone() - Shallow copy of the TreeMap instance

# How TreeMap works in java?
* TreeMap is a ***Red-Black tree based NavigableMap implementation***.

# Properties of Red Black tree:
* As the name of the algorithm suggests, color of every node in the tree is either red or black.
* Root node must be Black in color.
* Red node can not have a red color neighbor node.
* All paths from root node to the null should consist of the same number of black nodes.
* Rotations maintains the inorder ordering of the keys(x,y,z).
* A rotation can be maintained in O(1) time.

![red-black-tree]({{site.cdn}}/java/collections/red-black-tree.png)

# Why Treemap does not allow an initial size while HashMap does?
* HashMap re-hashes its buckets when new one gets inserted beyond the capacity.
* TreeMap does not reallocate nodes on adding new ones.
* Hence, size of the TreeMap dynamically increases if needed, without shuffling the internals.
