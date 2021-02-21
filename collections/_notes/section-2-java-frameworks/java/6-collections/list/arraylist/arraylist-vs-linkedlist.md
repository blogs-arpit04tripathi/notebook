---
layout: post
title: ArrayList vs LinkedList
permalink: /:collection/java/collections/arraylist-vs-linkedlist
---

- TOC
{:toc}

<hr><br>

|ArrayList				|LinkedList						|
|---					|---							|
|Resizable Array		|Douby-LinkedList				|
|						|ReverseIterator				|
|Initial capacity 10	|Constructs empty list			|
|Fast get, Random Access|Slower (traverses completly)	|
|Access - O(1)			|Access - O(n)					|
|Add – O(n), full array	|Add – O(n)						|
|Slow in comparision	|Fast add						|
|No	Memory Overhead		|Memory overhead (Node structure)|

|			|ArrayList	|LinkedList	|
|---		|---		|---		|
|Get		|O(1)		|O(n)		|
|Add		|O(1)		|O(1)		|
|Remove		|O(n)		|O(n)		|

# Similarities between ArrayList and LinkedList
* Not Synchronized
* clone(shallow copy)
* insertion order
* fail-fast iterator.

# When to Use ArrayList and LinkedList
* more frequently use ArrayList than LinkedList.
* ArrayList - more get(int) or search operations, O(1).
* LinkedList - more insert(int), delete(int) than get(int).