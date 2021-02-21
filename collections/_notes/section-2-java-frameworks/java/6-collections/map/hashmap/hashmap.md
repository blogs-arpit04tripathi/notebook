---
layout: post
title: HashMap
permalink: /:collection/java/collections/hashmap
---


* It uses a hash table to store the map. This allows the execution time of get( ) and put( ) to remain constant even for large sets. 
* The default capacity is 16. 
* The default fill ratio is 0.75.
* A hash map does not guarantee the order of its elements.
* The put( ) method automatically replaces any pre-existing value that is associated with the specified key with the new value.

```java
HashMap( )
HashMap(Map<? extends K, ? extends V> m)
HashMap(int capacity)
HashMap(int capacity, float fillRatio)
```

**What are different Collection views provided by Map interface?**  
- `Set<K> keySet()`	: Set view of the keys contained in this map
- `Collection<V> values()`	: Collection view of the values contained in this map
- `Set<Map.Entry<K, V>> entrySet()`	: Set view of the mappings contained in this map

* set/collection is backed by the map, so changes to the map are reflected in the set, and vice-versa. 
* If map modified while iteration over the set is in progress (except via iterator’s methods), results of iteration are undefined.
* The set supports element removal, mapping removed from map, via 
	- Iterator    - remove, 
	- Set    - remove, removeAll, retainAll, clear operations.
	- It does not support the add or addAll operations.
