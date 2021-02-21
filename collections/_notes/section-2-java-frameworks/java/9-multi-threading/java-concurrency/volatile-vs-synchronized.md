---
layout: post
title: volatile vs synchronized
permalink: /:collection/java/multithreading/volatile-vs-synchronized
---


* Two important features of locks and synchronization.
	1. **Mutual Exclusion**: Only one thread or process can execute a block of code (critical section) at a time.
	2. **Visibility**: It means that changes made by one thread to shared data are visible to other threads.
* **Synchronized**	: both mutual exclusion and visibility
* **Volatile**		: visibility and not atomicity

Characteristic|Synchronized|Volatile
---|---|---|
Type of target variable|Object|Object or primitive
null allowed?|No|Yes
Can block? (hold on to any lock)|Yes|No
All cached variables synchronized with main memory on access?|Yes|Yes
When synchronization happens|When you explicitly enter/exit a synchronized block|Whenever a volatile variable is accessed.
Can be used to make several operations as atomic operation?|Yes|	[Atomic get-set of volatiles](https://www.javamex.com/tutorials/synchronization_concurrency_7_atomic_updaters.shtml)
Used on	|variable, method, class	|variables only

> Read more about [cached variables synchronized](https://www.javamex.com/tutorials/synchronization_concurrency_synchronized2.shtml)

* x++ is a read-modify-write sequence of operations that must execute atomically.
* Because accessing a [volatile](https://www.javamex.com/tutorials/synchronization_volatile.shtml) variable **never holds a lock**, it is **not suitable** for cases where we want to ***read-update-write*** as an atomic operation (unless we're prepared to "miss an update");
* A volatile variable that is an object reference may be null (you're effectively synchronizing on the reference, not the actual object). Attempting to synchronize on a null object will throw a NullPointerException.
* Use of volatile keyword also prevents compiler or JVM from the reordering of code or moving away them from synchronization barrier.
* In Java, reads and writes are [atomic](https://javarevisited.blogspot.com/2012/02/what-is-race-condition-in.html) for all variables declared using [Java volatile keyword](https://javarevisited.blogspot.com/2011/06/volatile-keyword-java-example-tutorial.html) (including long and double variables).
* volatile keyword on variables reduces the risk of memory consistency errors as any write to a volatile variable in Java establishes a happens-before relationship with subsequent reads of that same variable.
* Java volatile keyword doesn't mean atomic, its common misconception that after declaring volatile ++ will be atomic, to make the operation atomic you still need to ensure exclusive access using synchronized method or block in Java.
* If a variable is not shared between multiple threads, you don't need to use volatile keyword with that variable.
volatile is not a replacement of synchronized keyword but can be used as an alternative in certain cases.
* The short time gap in between the reading of the volatile variable and the writing of its new value, creates an [race condition](http://tutorials.jenkov.com/java-concurrency/race-conditions-and-critical-sections.html) where multiple threads might read the same value of the volatile variable, generate a new value for the variable, and when writing the value back to main memory - overwrite each other's values. The situation where multiple threads are incrementing the same counter is exactly such a situation where a volatile variable is not enough.
