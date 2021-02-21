---
layout: post
title: Thread Priorities
permalink: /:collection/java/multithreading/thread-priorities
---


* A thread’s priority is used to decide when to switch from one running thread to the next, context switch. 
 
* The rules that determine when a context switch takes place are simple:
	- A thread can voluntarily relinquish control
		- explicitly yielding, sleeping, or blocking on pending I/O. 
		- Now, all other threads are examined, and the highest-priority thread that is ready to run is given the CPU.
	- A thread can be preempted by a higher-priority thread
		- Basically, as soon as a higher-priority thread wants to run, it does. This is called preemptive multitasking.
* When same priority threads are competing for CPU cycles, they are time-sliced automatically in round-robin fashion.

```java
final void setPriority(int level)        
final int getPriority( )
```

* static final variables in Thread class - **MIN_PRIORITY(1)**, **MAX_PRIORIT(10)** and **NORM_PRIORITY(5)**.
* Relying on preemptive behaviour causes most of the inconsistencies, instead of cooperatively giving up CPU time. 
* To obtain predictable cross-platform behaviour, use threads that voluntarily give up control of the CPU.
