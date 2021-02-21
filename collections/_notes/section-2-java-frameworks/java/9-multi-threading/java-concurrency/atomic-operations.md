---
layout: post
title: Atomic Operations
permalink: /:collection/java/multithreading/atomic-operations
---


* There is a branch of research focused on creating non-blocking algorithms (lock and wait-free algorithms) for concurrent environments. These algorithms exploit low-level atomic machine instructions such as ***compare-and-swap (CAS)***, to ensure data integrity.
* A typical CAS operation works on three operands:
	1. The memory location on which to operate (M)
	1. The existing expected value (A) of the variable
	1. The new value (B) which needs to be set
* ***The CAS operation updates atomically the value in M to B, but only if the existing value in M matches A, otherwise no action is taken***. In both cases, the existing value in M is returned. This combines three steps – getting the value, comparing the value and updating the value – into a single machine level operation.
* When multiple threads attempt to update the same value through CAS, one of them wins and updates the value. **However, unlike in the case of locks, no other thread gets suspended**; instead, they’re simply informed that they did not manage to update the value. The threads can then proceed to do further work and context switches are completely avoided.
* One other consequence is that the core program logic becomes more complex. This is because we have to handle the scenario when the CAS operation didn’t succeed. We can retry it again and again till it succeeds, or we can do nothing and move on depending on the use case.
