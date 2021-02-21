---
layout: post
title: Java Garbage Collection
permalink: /:collection/java/garbage-collection
---

- Process to identify and remove the unused objects from memory and free space. 
- Java has **automatic garbage collection**.
- **Garbage Collector**, background program that looks unreferenced objects, which are deleted to reclaim memory.
- Garbage collection involves three steps:
	- **Marking** – identifies objects not in use.
	- **Normal Deletion** - removes the unused objects and reclaim the free space.
	- **Deletion with Compacting** - For better performance, all survived objects moved together.
- Problems with simple mark and delete approach.
	- Not efficient, because most of the newly created objects will become unused.
	- Objects that are in-use for multiple garbage collection cycle are most likely to be in-use for future cycles too.
- Due to these problems, **Java Garbage Collection is Generational**.
  - we have **Young Generation** and **Old Generation** spaces in the heap memory.
