---
layout: post
title: TreeSet Class
permalink: /:collection/java/collections/treeset
---

* Creates a collection that uses a tree for storage. 
* Objects are stored in sorted, ascending order. 
* Access and retrieval times are quite fast, good choice when storing large sorted information that must be found quickly.

```java
TreeSet()
TreeSet(SortedSet<E> ss)
TreeSet(Collection<? extends E> c)
TreeSet(Comparator<? super E> comp)
```