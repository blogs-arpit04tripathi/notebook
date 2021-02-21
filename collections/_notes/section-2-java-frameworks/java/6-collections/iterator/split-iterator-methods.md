---
layout: post
title: Spliterators Methods
permalink: /:collection/java/collections/split-iterator-methods
---

|Spliterator||
|---|---
|boolean tryAdvance (Consumer<? super T> action)|false if no element left	|
|Spliterator\<T> trySplit( )|
|default Boolean hasCharacteristics(int val)|
|int characteristics( )|
|long estimateSize( )|elements left to iterate, else Long.MAX_VALUE
|default long getExactSizeIfKnown( ) |-1
|default void forEachRemaining(Consumer<? super T> action)	|
|default Comparator<? super T> getComparator( )	|null for natural ordering	

* **trySplit()** - original spliterator iterates one portion, while returned spliterator iterates other portion.