---
layout: post
title: Fail-Fast vs Fail-Safe Iterators
permalink: /:collection/java/collections/failfast-vs-failsafe-iterators
---

- TOC
{:toc}

<hr><br>

# Fail-Fast vs Fail-Safe
* Iterator fail-fast property checks for any modification in the structure of the underlying collection everytime we try to get the next element. If there are any modifications found, it throws **ConcurrentModificationException**.

|	|Fail-Fast	|Fail-Safe|
|---|---|---|
|package	|java.util|java.util.concurrent	|
|throws		|ConcurrentModificationException|	|
|Works with	|Original collection|Clone of underlying collection|
|collection	|By default all collections are fail-fast (ArrayList)|ConcurrentHashMap, CopyOnWriteArrayList|

**What is UnsupportedOperationException?**  
* `java.util.Collections.UnmodifiableCollection` throws this exception for all add and remove operations.

# Fail fast Iterator
**Scenarios for ConcurrentModificationException**  
* Single Threaded Environment - After iterator creation, structure modified by other iterator's own remove method. 
* Multiple Threaded Environments - one thread is iterating and other is modifying the structure.

**Is Fail Fast behaviour Guaranteed?**  
* According to [Oracle docs](https://docs.oracle.com/javase/7/docs/api/java/util/HashMap.html) , the fail-fast behavior of an iterator cannot be guaranteed as its impossible to make any concrete guarantees in the presence of unsynchronized concurrent modification. 
* Fail-fast iterators throw ***ConcurrentModificationException on a best-effort basis***.
* Fail-fast behavior of iterators should be used only to detect bugs. 

**How Fail Fast Iterator come to know that the internal structure is modified?**  
* Collections maintain an internal flag mods. 
* "mods" flag checked before every hasNext() and next().
* On any structural modification, mods flag changes, thus indicating iterator to throw ConcurrentModificationException.

# Fail Safe Iterator 
* Makes copy of the internal data structure (object array) and iterates over the copied data structure.
* Any structural modification doesn’t affect iterator hence, no ConcurrentModificationException.

**Two issues associated with Fail Safe Iterator are**  
* Overhead of maintaining the copied data structure i.e memory.
* No guarantee that data being read is the data currently in the original data structure.

```java
ConcurrentHashMap<String, String> map = new ConcurrentHashMap< >();
Iterator iterator = map.keySet().iterator();
```

* [Oracle docs](https://docs.oracle.com/javase/7/docs/api/java/util/concurrent/CopyOnWriteArrayList.html) , fail safe iterator is ordinarily too costly, efficient when traversal operations vastly outnumber mutations. 
* "snapshot" style iterator method uses a reference to the state of the array at the point that the iterator was created.
* This ***array never changes during the lifetime of the iterator, so interference is impossible and the iterator is guaranteed not to throw ConcurrentModificationException***.
* The iterator will not reflect additions, removals, or changes to the list since the iterator was created. 
* Mutating operations remove(), set(),add() are not supported on iterators. (**UnsupportedOperationException**)
