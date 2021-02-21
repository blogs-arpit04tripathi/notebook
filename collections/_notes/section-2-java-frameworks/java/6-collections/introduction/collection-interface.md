---
layout: post
title: Collection Interface
permalink: /:collection/java/collections/collection-interface
---

* Collection extends the **Iterable** interface hence can be cycled through using foreach style **for loop**.
* Collections ***can be modifiable and unmodifiable***, based on optional methods to do modification. Built-in collections are modifiable.
* Collections are made up of `(collection interfaces) + (Comparator, RandomAccess, Iterator, ListIterator and Spliterator interfaces)`.

|									|	|
|---								|---|
|**ClassCastException**				|	|
|**UnsupportedOperationException**	|	|
|**NullPointerException**			|attempt is made to store a null object and null elements are not allowed in the collection.|
|**IllegalArgumentException**		|thrown if an invalid argument is used.														|
|**IllegalStateException**			|When attempt is made to add an element to a fixed-length collection that is full.			|

![collection-interface]({{site.cdn}}/java/collections/collection-interface.png)
