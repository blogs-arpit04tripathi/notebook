---
layout: post
title: List Interface Methods
permalink: /:collection/java/collections/list-interface-methods
---

|List Interface Methods									|	|
|---													|---|
|void add(int index, E obj)								|	|
|boolean addAll(int index, Collection<? extends E> c)	|	|
|E remove(int index)									|	|
|default void replaceAll(UnaryOperator\<E> opToApply)	|	|
|E get(int index)										|	|
|E set(int index, E obj)								|	|
|int indexOf(Object obj)  -- default -1					|	|
|int lastIndexOf(Object obj)							|	|
|ListIterator\<E> listIterator( )						|	|
|ListIterator\<E> listIterator(int index)				|	|
|default void sort(Comparator<? super E>comp)			|	|
|List\<E> subList(int start, int end)  -- till end-1	|	|