---
layout: post
title: Array vs ArrayList
permalink: /:collection/java/collections/array-vs-arraylist
---

- TOC
{:toc}

<hr><br>

|Array					|ArrayList				|
|---					|---					|
|Fixed size				|resizable				|
|primitives	 			|Objects				|
|for, for each			|Iterator , for each	|
|.length				|size()					|
|Faster O(1)			|Slow in comparision	|
|Multidimensional		|No						|
|Assignment operator	|add method				|

* ArrayList provides features like addAll, removeAll, iterator etc.
* ArrayList is internally backed by array hence almost same performance for add or get operation.
* During ***resizing*** as it calls the native implemented method `System.arrayCopy(src, srcPos, dest, destPos, length)`.
* Worst case – array is full, for addition copy the data to new array of double size, ***might not find continuos memory locations***.
* In array, ***ArrayStoreException***, if try to store incompatible data type.

```java
String[] arrayobj = new String[3];
String temp[] = new String[2];		// creates a string array of size 2
temp[0] = new Integer(12);			// throws ArrayStoreException, trying to add Integer object in String[]
```

# Similarities between Array and ArrayList
- Allows Duplicate
- Allows null
- Insertion order
- Same performance for add/get.

# When to Use Array over ArrayList
* size of list is fixed, mostly used to store and traverse them.
* primitive data types (ArrayList slower due to auboxing and auto-unboxing).
* fixed multi-dimensional situation, using [ ][ ] is far more easier than `List<List<>>`.