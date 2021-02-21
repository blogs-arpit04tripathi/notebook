---
layout: post
title: MultivaluedMap<K,V>
permalink: /:collection/java/collections/multivaluedMap
---

* public interface MultivaluedMap<K,V> extends `java.util.Map<K, java.util.List<V>>`
* Nested Class - java.util.Map.Entry<K,V> 
* javax.ws.rs.core Interface
* A map of key-values pairs. ***Each key can have zero or more values***.

# Methods inherited from interface java.util.Map
clear, containsKey, containsValue, entrySet, equals, get, hashCode, isEmpty, keySet, put, putAll, remove, size, values

```java
public void get(@Context UriInfo ui) {
  MultivaluedMap params = ui.getRequestUri().getQuery();
  // now do what you want with your params
}
```

# List of Methods : MultivaluedMap

|MultivaluedMap Methods||
|---|---|
|Void add(K key, V value)       |Add a value to the current list of values for the supplied key.
|Void addAll(K key, List<V> valueList)||
|Void addAll(K key, V... newValues)||
|Void addFirst(K key, V value)  |Add a value to the first position in the current list of values for the supplied key.
|Boolean equalsIgnoreValueOrder(MultivaluedMap<K,V> otherMap)|Compare the specified map with this map for equality modulo the order of values for each key.|
|V getFirst(K key)              |A shortcut to get the first value of the supplied key.
|Void putSingle(K key, V value) |Set the key's value to be a one item list consisting of the supplied value.
