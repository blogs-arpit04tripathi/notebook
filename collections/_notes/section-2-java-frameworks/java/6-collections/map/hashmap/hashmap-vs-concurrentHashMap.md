---
layout: post
title: HashMap vs ConcurrentHashMap
permalink: /:collection/java/collections/hashmap-vs-concurrentHashMap
---


* `Collections.synchronizedMap(HashMap)` is equivalent to the HashTable object.
* When a modification is performed, Map is locked on Map object.
* ***ConcurrentHashMap*** synchronizes or ***locks at segment level rather than whole Map Object***.
* Optimized performance, Map is divided into different partitions depending upon the ***Concurrency level***.

# When to use TreeMap over HashMap 
* when key traversal in sorted order is required.
* Based on collection size, it is faster to add elements to HashMap and then convert to a TreeMap.

