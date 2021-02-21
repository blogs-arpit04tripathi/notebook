---
layout: post
title: Thread Class vs Runnable Interface
permalink: /:collection/java/multithreading/thread-vs-runnable
---

* **Thread** encapsulates a thread of execution. Since you can’t directly refer to the ethereal *state of a running thread, you will deal with it through its proxy, the Thread instance that spawned it*.

# Main Thread
* On program start-up, main thread begins running immediately, because it is the one that is executed when your program begins. 
* The main thread is important for two reasons: 
	- other “child” threads will be spawned from it.
	- performs various shutdown actions, must be the last thread to finish execution.
* main thread can be controlled using Thread object.

```java
Thread t = Thread.currentThread();
static void sleep(long milliseconds, int nanoseconds) throws InterruptedException
final void setName(String threadName)
final String getName( )
```

* **sleep( )** might throw an **InterruptedException** if some other thread wanted to interrupt this sleeping one.
**main thread default** name is **main**, priority **5**, and thread-group name **main**.

| Method    | Meaning          |
|---        |---|
getName 	|Obtain a thread’s name.
getPriority |Obtain a thread’s priority.
isAlive 	|Determine if a thread is still running.
join 	    |Wait for a thread to terminate.
run 	    |Entry point for the thread.
sleep 	    |Suspend a thread for a period of time.
start 	    |Start a thread by calling its run method.

* A *thread group* is a data structure that controls the state of a collection of threads as a whole.
