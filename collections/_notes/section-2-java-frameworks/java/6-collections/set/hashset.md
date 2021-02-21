---
layout: post
title: HashSet class
permalink: /:collection/java/collections/hashset
---


* Collection using a hash table for storage, via **hashing**. 
  * key hashcode decides index at which the data associated with the key is stored. 
  * With hashing, execution time of **add( ), contains( ), remove( )**, and **size( )** remain constant even for large sets. 
* ***Does not guarantee the order of its elements***. 
* For Sorted - ***TreeSet***.

```java
HashSet()
HashSet(Collection<? extends E> c)
HashSet(int capacity)
HashSet(int capacity, float fillRatio)
```

# Fill Ratio
* ***Range = 0.0 to 1.0***, defines the point where hashset needs to be resized upward. 
* Resize when `element count > (capacity x fill ratio)`.
* ***Default Value = 0.75***
