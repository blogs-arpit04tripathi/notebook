---
layout: post
title: Iterator Methods
permalink: /:collection/java/collections/iterator-methods
---

|Methods for Iterator|	|
|---|---|
|boolean hasNext( )     |
|E next( )              |NoSuchElementException
|default void remove( ) |IllegalStateException
|default void forEachRemaining(Consumer<? super E> action)	|