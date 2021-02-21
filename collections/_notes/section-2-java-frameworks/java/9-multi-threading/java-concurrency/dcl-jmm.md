---
layout: post
title: DCL - Meet the Java Memory Model
permalink: /:collection/java/multithreading/dcl-jmm
---

- TOC
{:toc}

<hr><br>

* More accurately, DCL is not guaranteed to work. To understand why, we need to look at the relationship between the JVM and the computer environment on which it runs. 
* Unlike most other languages, Java defines its relationship to the underlying hardware through a formal memory model that is expected to hold on all Java platforms, enabling Java's promise of "Write Once, Run Anywhere." 
* ***When running in a synchronous (single-threaded) environment***, a program's interaction with memory is quite simple, or at least it appears so. Programs store items into memory locations and expect that they will still be there the next time those memory locations are examined. Though we think of programs as executing sequentially -- in the order specified by the program code -- that doesn't always happen. Compilers, processors, and caches are free to take all sorts of liberties with our programs and data, as long as they don't affect the result of the computation. 
* For example, compilers can generate instructions in a different order from the obvious interpretation the program suggests and store variables in registers instead of memory; processors may execute instructions in parallel or out of order; and caches may vary the order in which writes commit to main memory. The JMM says that all of these various reorderings and optimizations are acceptable, so long as the environment maintains **as-if-serial semantics** -- that is, so long as you achieve the same result as you would have if the instructions were executed in a strictly sequential environment.
* ***With multithreaded programs***, the situation is quite different -- one thread can read memory locations that another thread has written. If thread A modifies some variables in a certain order, in the absence of synchronization, thread B may not see them in the same order -- or may not see them at all, for that matter. 
* That could result because 
	- the compiler reordered the instructions or temporarily stored a variable in a register and wrote it out to memory later; 
	- or because the processor executed the instructions in parallel or in a different order than the compiler specified; 
	- or because the instructions were in different regions of memory, and the cache updated the corresponding main memory locations in a different order than the one in which they were written.

Whatever the circumstances, multithreaded programs are inherently less predictable, unless you explicitly ensure that threads have a consistent view of memory by using synchronization.

# What does synchronized really mean?
* Java treats each thread as if it runs on its own processor with its own local memory, each talking to and synchronizing with a shared main memory. 
* Even on a single-processor system, that model makes sense because of the effects of memory caches and the use of processor registers to store variables. When a thread modifies a location in its local memory, that modification should eventually show up in the main memory as well, and the JMM defines the rules for when the JVM must transfer data between local and main memory. 
* The Java architects realized that an overly restrictive memory model would seriously undermine program performance. They attempted to craft a memory model that would allow programs to perform well on modern computer hardware while still providing guarantees that would allow threads to interact in predictable ways.
* Java's primary tool for rendering interactions between threads predictably is the ***synchronized*** keyword. Many programmers think of synchronized strictly in terms of **enforcing a mutual exclusion semaphore (mutex)** to prevent execution of critical sections by more than one thread at a time. Unfortunately, that intuition does not fully describe what synchronized means.
* The semantics of synchronized do indeed include mutual exclusion of execution based on the status of a semaphore, but they also include rules about the synchronizing thread's interaction with main memory. In particular, *the acquisition or release of a lock triggers a **memory barrier** -- a forced synchronization between the thread's local memory and main memory*. (Some processors -- like the Alpha -- have explicit machine instructions for performing memory barriers.) 
* When a thread exits a synchronized block, it performs a **write barrier** -- *it must flush out any variables modified in that block to main memory before releasing the lock*. 
* Similarly, when entering a synchronized block, it performs a **read barrier** -- *it is as if the local memory has been invalidated, and it must fetch any variables that will be referenced in the block from main memory*.
* The proper use of synchronization guarantees that one thread will see the effects of another in a predictable manner. Only when threads A and B synchronize on the same object will the JMM guarantee that thread B sees the changes made by thread A, and that changes made by thread A inside the synchronized block appear atomically to thread B (either the whole block executes or none of it does). 
* Furthermore, the JMM ensures that synchronized blocks that synchronize on the same object will appear to execute in the same order as they do in the program.

```java
Synchronized block = enforcing a mutual exclusion semaphore (mutex) + memory barrier
```

# So what's broken about DCL?
* DCL relies on an unsynchronized use of the resource field. That appears to be harmless, but it is not. 
* To see why, imagine that thread A is inside the synchronized block, executing the statement *resource = new Resource();* while thread B is just entering getResource(). Consider the effect on memory of this initialization. Memory for the new Resource object will be allocated; the constructor for Resource will be called, initializing the member fields of the new object; and the field resource of SomeClass will be assigned a reference to the newly created object.

However, since thread B is not executing inside a synchronized block, it may see these memory operations in a different order than the one thread A executes. It could be the case that B sees these events in the following order (and the compiler is also free to reorder the instructions like this): allocate memory, assign reference to resource, call constructor. Suppose thread B comes along after the memory has been allocated and the resource field is set, but before the constructor is called. It sees that resource is not null, skips the synchronized block, and returns a reference to a partially constructed Resource! Needless to say, the result is neither expected nor desired.

When presented with this example, many people are skeptical at first. Many highly intelligent programmers have tried to fix DCL so that it does work, but none of these supposedly fixed versions work either. It should be noted that DCL might, in fact, work on some versions of some JVMs -- as few JVMs actually implement the JMM properly. However, you don't want the correctness of your programs to rely on implementation details -- especially errors -- specific to the particular version of the particular JVM you use.

Other concurrency hazards are embedded in DCL -- and in any unsynchronized reference to memory written by another thread, even harmless-looking reads. Suppose thread A has completed initializing the Resource and exits the synchronized block as thread B enters getResource(). Now the Resource is fully initialized, and thread A flushes its local memory out to main memory. The resource's fields may reference other objects stored in memory through its member fields, which will also be flushed out. While thread B may see a valid reference to the newly created Resource, but as it didn't perform a read barrier it could still see stale values of resource's member fields.

# Volatile doesn't mean what you think, either
A commonly suggested nonfix is to declare the resource field of SomeClass as volatile. However, while the JMM prevents writes to volatile variables from being reordered with respect to one another and ensures that they are flushed to main memory immediately, it still permits reads and writes of volatile variables to be reordered with respect to nonvolatile reads and writes. That means -- unless all Resource fields are volatile as well -- thread B can still perceive the constructor's effect as happening after resource is set to reference the newly created Resource.

# Alternatives to DCL

* The most effective way to fix the DCL idiom is to avoid it. The simplest way to avoid it, of course, is to use **synchronization**. Whenever a variable written by one thread is being read by another, you should use synchronization to guarantee that modifications are visible to other threads in a predictable manner.
* **Another option** for avoiding the problems with DCL is to drop lazy initialization and instead **use eager initialization**. Rather than delay initialization of resource until it is first used, initialize it at construction. The **class loader**, which synchronizes on the classes' Class object, **executes static initializer blocks at class initialization time**. That means that the effect of static initializers is automatically visible to all threads as soon as the class loads.
