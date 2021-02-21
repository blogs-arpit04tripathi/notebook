---
layout: post
title: Set Interface
permalink: /:collection/java/collections/set-interface
---

* Does not allow duplicate elements. 
* add( ) - returns false if attempt to add duplicate elements to a set.

|SortedSet Interface					|				|	|
|---									|---			|---|
|E first( ) 							|
|E last( )								|
|Comparator<? super E> comparator( )	|
|SortedSet\<E> headSet(E end) 			|`for < end`	|
|SortedSet\<E> tailSet(E start)  		|`for >= start`	|
|SortedSet\<E> subSet(E start, E end) 	|`till end-1`	|

|NavigableSet Interface										|							|
|---														|---						|
|Iterator<E> descendingIterator( )							|
|NavigableSet<E> descendingSet( )							|
|E ceiling(E obj)  											|smallest element e >= obj	|
|E floor(E obj)  											|largest element e <= obj.	|
|E lower(E obj)  											|largest element e < obj.	|
|E higher(E obj)       										|smallest element e > obj.	|
|E pollFirst( )  											|null (if empty)			|
|E pollLast( ) 												|							|
|headSet(E upperBound, boolean incl)						|`< upper`					|
|tailSet(E lowerBound, boolean incl)						|`> lower`					|
|subSet(E lower, boolean lowIncl,E upper, boolean highIncl)	|							|
