---
layout: post
title: Deque Interface
permalink: /:collection/java/collections/dequeue-interface
---

* a double-ended queue. 
* can function as standard FIFO queues or as LIFO stacks.

# List of Methods : Deque Interface

|Deque Interface							|	|
|---										|---|
|void addFirst(E obj)						|IllegalStateException, if queue full			|
|void addLast(E obj)						|IllegalStateException, if queue full			|
|boolean offerFirst(E obj)					|
|boolean offerLast(E obj)					|
|E getFirst( )								|not removed, NoSuchElementException if empty	|
|E getLast( )								|not removed, NoSuchElementException if empty	|
|E peekFirst( )								|head, not removed. null if empty.				|
|E peekLast( )								|tail, not removed. null if empty.				|
|E pollFirst( )								|head, removed. null if empty.					|
|E pollLast( )								|tail, removed. null if empty.					|
|void push(E obj)							|adds head, IllegalStateException if full.		|
|E pop( )									|head, removed. NoSuchElementException if empty.|
|E removeFirst( )							|head, removed. NoSuchElementException			|
|E removeLast( )							|tail, removed. NoSuchElementException			|
|Boolean removeFirstOccurrence(Object obj)	|
|Boolean removeLastOccurrence(Object obj)	|
|Iterator<E> descendingIterator( )			|	