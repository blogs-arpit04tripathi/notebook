---
layout: post
title: ConcurrentHashMap
permalink: /:collection/java/collections/concurrentHashMap
---

* ConcurrentHashMap utilizes the same principles of HashMap, but for a multi-threaded application. 
* It does not require explicit synchronization.
* Hashtable provides concurrent access to the Map.Entries by locking the entire map. Hence performance is impacted.
* Provides the same functionality as of Hashtable but with a performance comparable to HashMap.
* **Bucket/Segment Level Lock rather than Object Level**.

```java
static final int DEFAULT_INITIAL_CAPACITY = 16;
static final int DEFAULT_CONCURRENCY_LEVEL = 16;
```

![concurrent-hashmap]({{site.cdn}}/java/collections/concurrent-hashmap.png)

```java
public ConcurrentHashMap(int initialCapacity, float loadFactor, int concurrencyLevel)
```

|	|	|
|---|---|
|initialCapacity 	|initial capacity, by default 16.|
|concurrencyLevel	|estimated number of concurrently updating threads, by default 16.|

* By default, ConcurrentHashMap maintains 16 locks for 16 buckets of the Map. 
* At max 16 threads (concurrency level) can modify the collection at the same time, if each thread works on different bucket. 
* get() do not block, so may overlap with update operations (put and remove). 
* Retrievals reflect the results of the most recently completed update operations holding upon their onset. 
* Ideally, you should choose a value to accommodate as many threads as will ever concurrently modify the table. Using a significantly higher value than you need can waste space and time, and a significantly lower value can lead to thread contention.
