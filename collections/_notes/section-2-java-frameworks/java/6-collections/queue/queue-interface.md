---
layout: post
title: Queue Interface
permalink: /:collection/java/collections/queue-interface
---

* first-in, first-out list. (FIFO)
* Elements can only be removed from the head of the queue.

|   ||
|---|---|
|boolean offer(E obj)	| add obj to queue, true or false.  (For fixed length queue, it can be false)	|
|E peek( ) 				| return head. <br>Null for empty												|
|E poll( ) 				| remove and return head. <br>Null for empty									|
|E element( )			| return head. <br>NoSuchElementException for empty								|
|E remove( ) 			| remove and return head. <br>NoSuchElementException for empty					|

**What is the difference between peek(),poll() and remove() method of the Queue interface?**  
* poll() - remove head object of the Queue. If Queue is empty, return null.
* remove() - remove head object of the Queue. If Queue is empty throw NoSuchElementException. 
* peek() - retrieves but does not remove the head of the Queue. If queue is empty then peek() method also returns null.