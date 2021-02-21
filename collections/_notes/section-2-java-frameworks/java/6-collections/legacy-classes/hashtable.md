---
layout: post
title: Hashtable
permalink: /:collection/java/collections/hashtable
---


```java
Hashtable( )
Hashtable(int size)
Hashtable(int size, float fillRatio)
Hashtable(Map<? extends K, ? extends V> m)
```

* **Hashtable** was implementation of a **Dictionary**. 
* Hashtable was reengineered to also implement the **Map** interface. 
* It is similar to **HashMap**, but is synchronized.
* Neither keys nor values can be **null**, **NullPointerException**.
* Key is hashed, and hash code is used as the index at which the value is stored within the table.
* A hash table takes objects that override the **hashCode( )** and **equals( )** methods of **Object**. 
* The default size is 11. 
* Default fill Ratio is 0.75.

|Methods|||
---|---|---
void clear( )|Enumeration<V> elements( )|void rehash( ) 
Object clone( )|V get(Object key)|V remove(Object key) 
boolean contains(Object value)|boolean isEmpty( )|int size( ) 
boolean containsKey(Object key)|Enumeration<K> keys( )|String toString( ) 
boolean containsValue(Object value)|V put(K key, V value) 
