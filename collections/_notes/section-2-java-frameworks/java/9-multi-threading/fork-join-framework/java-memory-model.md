---
layout: post
title: Java Memory Model
permalink: /:collection/java/multithreading/java-memory-model
---

- TOC
{:toc}

<hr><br>

> Read more about [Java Memory Model (JMM)](http://tutorials.jenkov.com/java-concurrency/java-memory-model.html)

- Java memory model(JMM) - specifies how the Java virtual machine works with the computer's memory (RAM).
- JMM specifies how and when different threads can see values written to shared variables, and how to synchronize access to shared variables when necessary.

# Internal Java Memory Model

- JMM is used internally in JVM
- It divides memory between thread stacks and the heap.
- Each thread running in the JVM has its own thread stack
	- contains info of methods called to reach the current point of execution. (call stack)
	- contains all local variables for each method being executed (on the call stack). 
- A thread can only access its own thread stack and each thread has its own version of each local variable.
- Local variables
	- primitive type, its totally kept on the thread stack. (not visible to other threads)
	- reference to an object, reference stored on the thread stack, but the object itself if stored on the heap.
- An object's member variables are stored on the heap along with the object itself.
- Static class variables are also stored on the heap along with the class definition.
- 2 threads calling same method of object at the same time, both will have access to the object's member variables, but each thread will have its own copy of the local variables.

![jmm]({{site.cdn}}/java/multi-threading/jmm.png)

# Hardware Memory Architecture

- Modern computer often has 2 or more CPUs in it. 
- Some CPU may have multiple cores hence more than 1 thread can run. 
- Consider, each CPU can run 1 thread at a time.
- Each CPU contains a set of registers in-CPU memory and CPU cache memory.
- Some CPUs may have multiple cache layers (Level 1 and Level 2) also.
- All CPUs can access the main memory area of computer (RAM).
- CPU will read part of main memory into its CPU cache and may even read part of the cache into its internal registers and then perform operations on it. 
- For write operations, result will flush from internal register to cache memory, and at some point, flushed back to main memory.
- values from cache memory are typically flushed back to main when the CPU needs to store something else in the cache.
- CPU cache can have data written to part of its memory at a time, and flush part of its memory at a time. 
- It does not have to read / write the full cache each time it is updated. 
- Cache is updated in smaller memory blocks called "**cache lines**". One or more cache lines may be read into the cache memory, and one or more cache lines may be flushed back to main memory.

![hardware-memory-architecture]({{site.cdn}}/java/multi-threading/hardware-memory-architecture.png)

# Bridging the Gap Between JMM And Hardware Memory Architecture

- JMM and the hardware memory architecture are different.
- Hardware memory architecture does not distinguish between thread stacks and heap as both the thread stack and the heap are located in main memory. Parts of the thread stacks and heap may sometimes be present in CPU caches and in internal CPU registers.

![jmm-hardware-mapping]({{site.cdn}}/java/multi-threading/jmm-hardware-mapping.png)

- When objects and variables can be stored in various different memory areas in the computer, certain problems may occur. 
- The two main problems are:
	- Visibility of thread updates (writes) to shared variables.
	- Race conditions when reading, checking and writing shared variables.

# Visibility of Shared Objects

- Without ***volatile declarations*** or ***synchronization***, updates to shared object by 1 thread may not be visible to others and each thread may end up having its own copy of the shared object sitting in its CPU cache.
- ***Solution*** - use [volatile keyword](http://tutorials.jenkov.com/java-concurrency/volatile.html), makes sure that the shared variable is read directly from main memory, and always written back to main memory when updated.

![shared-object-visibility-default]({{site.cdn}}/java/multi-threading/shared-object-visibility-default.png)
![shared-object-visibility-volatile]({{site.cdn}}/java/multi-threading/shared-object-visibility-volatile.png)

# Race Conditions

- If more than one thread updates variables in that shared object, [race conditions](http://tutorials.jenkov.com/java-concurrency/race-conditions-and-critical-sections.html) may occur.
- Example, 2 threads incrementing count concurrently without proper synchronization. updated value will only be 1 higher than the original value, despite the two increments.
- **Solution** – use [synchronized block](http://tutorials.jenkov.com/java-concurrency/synchronized.html) which guarantees 
	- only one thread can enter a given critical section of code at any given time 
	- all variables accessed inside the synchronized block will be read directly from main memory
	- when thread exits synchronized block, all updated variables will be flushed back to main memory again, regardless of whether the variable is declared volatile or not.
