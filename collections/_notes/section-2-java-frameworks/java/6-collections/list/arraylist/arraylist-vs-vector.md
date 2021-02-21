---
layout: post
title: ArrayList vs Vector
permalink: /:collection/java/collections/arraylist-vs-vector
---


|ArrayList				|Vector									|
|---					|---									|
|						|legacy, Synchronized, Thread-Safe		|							|
|Fast					|Slow (due to synchronize overhead)		|
|50% increase			|100%									|
|Set Increment Size - No|public synchronized void setSize(int i)|
|Iterator				|Enumerator								|
|Default size - 10		|										|

# Similarities ArrayList and Vector
- index based
- backed up by an array internally
- insertion order
- allow nulls