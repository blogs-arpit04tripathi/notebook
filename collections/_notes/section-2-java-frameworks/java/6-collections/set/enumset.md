---
layout: post
title: EnumSet Class
permalink: /:collection/java/collections/enumset
---


* For use with elements of an **enum** type from a single enum
* **EnumSet** defines no constructors, but uses factory methods. 
* of() - overloaded many times. known arguments count is faster than varargs.
* Not synchronized 
* Null not allowed - can throw NullPointerException.
* **Fail-safe iterator**, never throws ***ConcurrentModificationException*** and is ***weakly consistent***.

```java
class EnumSet<E extends Enum<E>>
static <E extends Enum<E>> EnumSet<E>
```

|EnumSet Methods|	|
|---							|---|
|allOf(Class\<E> t)				|
|complementOf(EnumSet\<E> e)	|
|of(E v)						|
|of(E v1, E v2)					|
|of(E v1, E v2, E v3)			|
|of(E v1, E v2, E v3, E v4)		|
|of(E v1, E v2, E v3, E v4,E v5)|
|of(E v, E … varargs)			|
|copyOf(Collection\<E> c)		|
|copyOf(EnumSet\<E> c) 			|IllegalArgumentException	|
|noneOf(Class\<E> t)			|	|
|range(E start, E end) 			|IllegalArgumentException|

# Advantage over HashSet
* constant time execution for all basic operations. 
* Much faster than HashSet counterparts as hashcode can be cached.
