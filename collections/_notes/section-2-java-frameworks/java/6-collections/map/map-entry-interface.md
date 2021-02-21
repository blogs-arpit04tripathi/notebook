---
layout: post
title: Map.Entry Interface
permalink: /:collection/java/collections/map-entry-interface
---

* **entrySet()** - returns a Set containing the map entries. **(Map.Entry)**
* **comparingByKey()**, which returns a Comparator that compares entries by key. 
* **comparingByValue()**, which returns a **Comparator** that compares entries by value.

```java
int hashCode( )
K getKey( ) 
V getValue( ) 
boolean equals(Object obj)
V setValue(V v)
	- ClassCastException (incompatible),
	- IllegalArgumentException,
	- NullPointerException (not nullable),
	- UnsupportedOperationException (unmodifiable)
```