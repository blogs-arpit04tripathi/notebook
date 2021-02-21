---
layout: post
title: Vector
permalink: /:collection/java/collections/vector
---

* **Vector** - dynamic array, synchronized
* Vector is reengineered to extend **AbstractList** and to implement **List** and **Iterable**. 
* Now, Vector can have its contents iterated by the enhanced for loop.
* protected int **capacityIncrement**: how much to increase on resized, default doubled.
* protected int elementCount
* protected Object[] elementData
* Automatically allocates extra room for additional objects, reduces allocation cycles.

```java
Vector( )
Vector(int size)
Vector(int size, int incr)
Vector(Collection<? extends E> c)
```

|	|	|
|---|---|
|void addElement(E element) 	|E lastElement( ) 
|int capacity( ) 	|int lastIndexOf(Object element) 
|Object clone( ) 	|int lastIndexOf(Object element, int start)
|boolean contains(Object element)|void removeAllElements( ) 
|void copyInto(Object array[ ])	|boolean removeElement(Object element) 
|E elementAt(int index) |void removeElementAt(int index) 
|Enumeration<E> elements()|void setElementAt(E element, int index)
|void ensureCapacity(int size)|void setSize(int size) 
|E firstElement( ) 		|int size( ) 
|int indexOf(Object element)|String toString( ) 
|int indexOf(Object element, int start)		|void trimToSize( ) 
|void insertElementAt(E element, int index)	|boolean isEmpty( )
