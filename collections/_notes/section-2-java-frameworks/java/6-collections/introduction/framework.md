---
layout: post
title: Collections Framework
permalink: /:collection/java/collections/framework
---

- TOC
{:toc}

<hr><br>

# Introduction
* **Framework** - Represents set of classes and interface providing readymade architecture.
* Java Collections framework - to store and manipulate the group of objects in a standardized way.
* Collection - represents a single unit of objects i.e. a group.
* All data operations can be performed by Java Collections - searching, sorting, insertion, manipulation, deletion etc.. 
* `java.util.*` package

# Collections Framework Goals
* High-performance
* Interoperatbility 
* Easy to adapt or extend - standard implementations.

# Benefits of collections framework
* Reduced development effort.
* enhanced code quality, already well tested.
* Reduced code maintenance efforts, shipped with JDK.
* Reusability and Interoperability

![colelctions]({{site.cdn}}/java/collections/collections.png)

* **Collections** class – contains static method **Algorithms** for collections. (generic)
* **iterator** - standardized way of accessing the elements of a collection, provides a means of ***enumerating its contents***. 
* JDK 8 
	- a **Spliterator** parallel iteration. 
	- iterator interfaces for primitive types, **PrimitiveIterator** and **PrimitiveIterator.OfDouble**.
* Collections framework also defines several map interfaces and classes. 

# Are Maps Collection?
**If not, why put them in Collections Framework?**  
* Maps are part of Collections Framework, but they are not “collections” in the strict use of the term.
* You can obtain a collection-view of a map.
* Maps - store key/value pairs.
* Eventually they also represent a way of effectively storing the data hence kept in collection framework.