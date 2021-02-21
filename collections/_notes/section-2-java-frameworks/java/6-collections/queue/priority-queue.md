---
layout: post
title: PriorityQueue Class
permalink: /:collection/java/collections/priority-queue
---

* Creates a queue that is prioritized based on the queue’s comparator. 
* PriorityQueues are dynamic, growing as necessary.
* An unbounded queue based on a priority heap.
* Elements are ordered in their natural order or provided Comparator. 
* Null not allowed.
* Must be comparable or otherwise comparator is required. 
* Not thread-safe and provided ***O(log(n)) time for enqueing and dequeing operations***.

|Constructors								|	|	|
|---										|---|---|
|PriorityQueue( )							|PriorityQueue(int capacity)					|
|PriorityQueue(Collection<? extends E> c)	|PriorityQueue(PriorityQueue<? extends E> c)	|PriorityQueue(SortedSet<? extends E> c)|
|PriorityQueue(Comparator<? super E> comp)	|PriorityQueue(int capacity, Comparator<? super E> comp)||

* default comparator - ascending order. head is smallest value.
* Comparator<? super E> **comparator()** - returns the comparator, **null** for natural ordering.
* You can iterate through a PriorityQueue using an iterator, the order of that iteration is undefined.
* To properly use **PriorityQueue**, call methods **offer(), poll( )** defined by the ***Queue*** interface.