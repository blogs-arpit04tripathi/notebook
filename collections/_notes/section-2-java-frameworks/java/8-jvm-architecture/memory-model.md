---
layout: post
title: Java Memory Model
permalink: /:collection/java/memory-model
---

- TOC
{:toc}

<hr><br>

![java-memory-model]({{site.cdn}}/java/jvm-architecture/java-memory-model.png)
![jmm-diagram]({{site.cdn}}/java/jvm-architecture/jmm-diagram.png)

- JVM Heap memory is divided into two parts – **Young Generation** and **Old Generation**.

# Young Generation
- **Eden Memory** and **two Survivor Memory spaces (S0 and S1)**
- **Eden Memory**
  - Most of the newly created objects.
  - **Minor GC** is performed when Eden space is filled and survivor objects are moved to S0.
  - Minor GC also checks S0 and move them to S1.
  - So, at a time one of the survivor space is always empty.
- Objects that survived after many cycles of GC, are moved to the Old generation memory space.
- A threshold is set for the age of the young generation objects to become eligible for promotion to Old generation.

# Old Generation
* Contains objects that are long lived and survived after many rounds of Minor GC. 
* Usually garbage collection is performed in Old Generation memory when it’s full.
* Old Generation Garbage Collection is called **Major GC** and usually takes longer time.

### Stop the World Event
- All the Garbage Collections are “Stop the World” events as all application threads are stopped until operation completes.
- Minor GC is very fast and the application doesn’t get affected by this.
- Major GC takes longer time because it checks all the live objects, hence should be minimized.
- Duration taken by garbage collector depends on the strategy used for garbage collection.
  - That’s why it’s necessary to monitor and tune the garbage collector to avoid timeouts in the highly responsive applications.

# Perm Gen or Method Area
- Not a part of Java Heap memory.
- Populated by JVM at runtime based on the classes used by the application.
  - contains Java SE library classes and methods. 
  - stores class structure (runtime constants and static variables) and code for methods and constructors.
- Perm Gen objects are garbage collected in a full garbage collection.
- **Memory Pool**
	- Created by JVM memory managers to create a pool of immutable objects, if implementation supports it.
	- String Pool is a good example of this kind of memory pool. 
	- Memory Pool can belong to Heap or Perm Gen, depending on the JVM memory manager implementation.
- **Runtime Constant Pool**
	- Runtime constant pool is per-class runtime representation of constant pool in a class. 
	- It contains class runtime constants and static methods.
	- Runtime constant pool is the part of method area.
- **Java Stack Memory**
	- Java Stack memory is used for execution of a thread.
    - contain method specific values that are short-lived and references to other objects on the heap referred from method.
