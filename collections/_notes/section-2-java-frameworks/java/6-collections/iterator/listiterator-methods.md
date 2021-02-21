---
layout: post
title: ListIterator Methods
permalink: /:collection/java/collections/listiterator-methods
---

|Methods for ListIterator||
|---|---|
|boolean hasNext( )		|
|E next( )				|
|boolean hasPrevious( )	|
|E previous( ) 			|
|int nextIndex( )		|No next element, return size|
|int previousIndex( )	|No prev, return -1|
|void add(E obj)		|
|void remove( )			|IllegalStateException, next()/previous() req	|
|void set(E obj)		|IllegalStateException, next()/previous() req	|
|default void forEachRemaining (Consumer<? super E> action)	|	|