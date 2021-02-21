---
layout: post
title: HashMap vs HashTable
permalink: /:collection/java/collections/hashmap-vs-hashtable
---


|				|HashMap		|Hashtable
|---			|---			|---
|Synchronized	|No				|Yes
|Thread-Safe	|No				|Yes
|Null Keys		|One null key	|No
|Null values	|Any null values|No
|Iteration		|Iterator		|Enumerator
|Iterator type	|Fail fast iterator	|Fail safe iterator
|Performance	|Fast			|Slow in comparison
|Superclass 	|AbstractMap	|Dictionary
|Legacy			|No				|Yes

 
# When to use HashMap and Hashtable?
* Unsynchronized/single threaded- Use HashMap in.
* Multithreaded - Hashtable/ConcurrentHashMap.
  * Java 8, ConcurrentHashMap used rather than HashTable.

# Similarities between HashMap and Hashtable
* Do not guarantee insertion order
* based on hashing
* constant time performance(put/get)
