---
layout: post
title: Terminal Operations
permalink: /:collection/java/java8/streams/operations/terminal
---

* return a result of a certain type, Stream.forEach or IntStream.sum
* After the terminal operation is performed, the stream pipeline is considered consumed, and can no longer be used.
* If you need to traverse the same data source again, you must return to the data source to get a new stream.
* Generally, terminal operations are eager. Only the terminal operations *iterator()* and *spliterator()* are not eager. 
