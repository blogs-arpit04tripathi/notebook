---
layout: post
title: LinkedHashMap
permalink: /:collection/java/collections/linkedHashMap
---


* It maintains a linked list of the entries in the map. This allows insertion-order iteration over the map.
* The default capacity is **16**. 
* The default fill-ratio is **0.75**.
* *Order* flag
  * ***true*** : access order is used.
  * ***false***: insertion order is used. 

```java
LinkedHashMap( )
LinkedHashMap(Map<? extends K, ? extends V> m)
LinkedHashMap(int capacity)
LinkedHashMap(int capacity, float fillRatio)
LinkedHashMap(int capacity, float fillRatio, boolean Order)
```

**LinkedHashMap** adds only one method to those defined by **HashMap**
* protected boolean `removeEldestEntry(Map.Entry<K, V> e)` 
* This method is called by **put( )** and **putAll( )**. The oldest entry is passed in e. 
* By default, this method returns **false** and does nothing. To use it, you override this method.
* Have your override return **true** to remove. To keep the oldest entry, return **false**.
