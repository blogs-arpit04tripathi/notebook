---
layout: post
title: Concurrent Collection FAQ
permalink: /:collection/java/collections/concurrent-collection-faq
---


**Which collection classes are thread-safe?**  
* Vector, Hashtable, Properties, Stack. 
* Concurrent API allows modification of collection while iteration because they work on the clone of the collection.

**What are concurrent Collection Classes?**  
* java.util.concurrent contains thread-safe collection classes that allow collections to be modified while iterating. 
* Java.util - Iterator implementation are fail-fast and throw **ConcurrentModificationException**. 
* java.util.concurrent  - Iterator implementation is fail-safe and we can modify the collection while iterating.
* exmaples - CopyOnWriteArrayList, ConcurrentHashMap, CopyOnWriteArraySet.

**How can we create a synchronized collection from given collection?**  
Collections.synchronizedCollection(Collection c)

**Can two threads update the ConcurrentHashMap simultaneously?**  
* Yes, if on different buckets/segments.
* No, if on same bucket/segment.

**Why ConcurrentHashMap does not allow null keys and null values?**  
* Not allowed due to ambiguities in **ConcurrentHashMaps**, **ConcurrentSkipListMaps**. 
* map.get(key) returns null, can’t find if value is null or the key isn't mapped. 
* In non-concurrent map, map.contains(key) can be used, but in a concurrent one, the map might have changed between calls.
* key k might be deleted in between the get(k) and containsKey(k) calls.

```java
if (map.containsKey(k)) 
    return map.get(k);
else
   throw new KeyNotPresentException();
```

