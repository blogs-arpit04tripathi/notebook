---
layout: post
title: Collection Interface Methods
permalink: /:collection/java/collections/collection-interface-methods
---


|collection operations						|		|
|---										|---|
|boolean add(E obj) 						| boolean addAll(Collection<? extends E> c)					|
|boolean remove(Object obj)					| boolean removeAll(Collection<?> c)						|
| default boolean removeIf(Predicate<? super E> predicate)	|
|boolean contains(Object obj)				| boolean containsAll(Collection<?> c)						|
|int size( )								| boolean isEmpty( )										|
|void clear( )								| boolean retainAll(Collection<?> c)						|
|boolean equals(Object obj)					| int hashCode( )											|					
|Iterator<E> iterator( )					| default Spliterator<E> spliterator( )						|
|Object[ ] toArray()						|<T> T[ ] toArray(T array[ ])<br> ArrayStoreException, if any collection element has a type that is not a subtype of array.|
|default Stream<E> stream()					| default Stream<E> parallelStream( )						|

* **stream()** and **parallelStream()** - return a **Stream** that uses the collection as a source of elements.
