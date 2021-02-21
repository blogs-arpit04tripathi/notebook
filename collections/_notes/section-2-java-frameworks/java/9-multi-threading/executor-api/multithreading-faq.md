---
layout: post
title: Multithreading FAQ
permalink: /:collection/java/multithreading/multithreading-faq
---

- TOC
{:toc}

<hr><br>

# How can we achieve thread safety in Java?
There are several ways to achieve thread safety in java – synchronization, atomic concurrent classes, implementing concurrent Lock interface, using volatile keyword, using immutable classes and Thread safe classes.

# What is Java Thread Dump, How can we get Java Thread dump of a Program?
Thread dump is list of all the threads active in the JVM, thread dumps are very helpful in analyzing bottlenecks in the application and analyzing deadlock situations. There are many ways using which we can generate Thread dump – Using Profiler, Kill -3 command, jstack tool etc. I prefer jstack tool to generate thread dump of a program because it’s easy to use and comes with JDK installation. Since it’s a terminal based tool, we can create script to generate thread dump at regular intervals to analyze it later on. Read this post to know more about [generating thread dump in java](https://www.journaldev.com/1053/java-thread-dump-visualvm-jstack-kill-3-jcmd).

# What is Deadlock? How to analyse and avoid deadlock situation?
Deadlock is a programming situation where two or more threads are blocked forever, this situation arises with at least two threads and two or more resources.

To analyse a deadlock, we need to look at the java thread dump of the application, we need to look out for the threads with state as BLOCKED and then the resources it’s waiting to lock, every resource has a unique ID using which we can find which thread is already holding the lock on the object.

Avoid Nested Locks, Lock Only What is Required and Avoid waiting indefinitely are common ways to avoid deadlock situation, read this post to learn how to [analyze deadlock in java](https://www.journaldev.com/1058/deadlock-in-java-example) with sample program.

# What is Java Timer Class? How to schedule a task to run after specific interval?
- java.util.Timer is a utility class that can be used to schedule a thread to be executed at certain time in future. Java Timer class can be used to schedule a task to be run one-time or to be run at regular intervals.
- java.util.TimerTask is an [abstract class](https://www.journaldev.com/1582/abstract-class-in-java) that implements Runnable interface and we need to extend this class to create our own TimerTask that can be scheduled using java Timer class.
- [java Timer example](https://www.journaldev.com/1050/java-timer-timertask-example).

# What is Lock interface in Java Concurrency API? What are it’s benefits over synchronization?
> Read more at [Java Lock Example](https://www.journaldev.com/2377/java-lock-example-reentrantlock).

Lock interface provide more extensive locking operations than can be obtained using synchronized methods and statements. They allow more flexible structuring, may have quite different properties, and may support multiple associated Condition objects.

The advantages of a lock are
	- it’s possible to make them fair
	- it’s possible to make a thread responsive to interruption while waiting on a Lock object.
	- it’s possible to try to acquire the lock, but return immediately or after a timeout if the lock can’t be acquired
	- it’s possible to acquire and release locks in different scopes, and in different orders

# What is BlockingQueue? How can we implement Producer-Consumer problem using Blocking Queue?
> Read more about [producer-consumer problem implementation using BlockingQueue](https://www.journaldev.com/1034/java-blockingqueue-example).

* java.util.concurrent.BlockingQueue is a Queue that supports operations that wait for the queue to become non-empty when retrieving and removing an element, and wait for space to become available in the queue when adding an element.
* BlockingQueue doesn’t accept null values and throw NullPointerException if you try to store null value in the queue.
* BlockingQueue implementations are thread-safe. All queuing methods are atomic in nature and use internal locks or other forms of concurrency control.
* BlockingQueue interface is part of [java collections framework](https://www.journaldev.com/1260/collections-in-java-tutorial) and it’s primarily used for implementing producer consumer problem.

# What is FutureTask Class?
FutureTask is the base implementation class of Future interface and we can use it with Executors for asynchronous processing. Most of the time we don’t need to use FutureTask class but it comes real handy if we want to override some of the methods of Future interface and want to keep most of the base implementation. We can just extend this class and override the methods according to our requirements. Check out [Java FutureTask Example](https://www.journaldev.com/1650/java-futuretask-example-program) post to learn how to use it and what are different methods it has.

# What are Concurrent Collection Classes?
> Read more about [how to avoid ConcurrentModificationException when using iterator](https://www.journaldev.com/378/java-util-concurrentmodificationexception)

* Java Collection classes are fail-fast which means that if the Collection will be changed while some thread is traversing over it using iterator, the iterator.next() will throw ConcurrentModificationException.
* Concurrent Collection classes support full concurrency of retrievals and adjustable expected concurrency for updates.
* Major classes are ConcurrentHashMap, CopyOnWriteArrayList and CopyOnWriteArraySet.

# What is Executors Class?
* Executors class provide utility methods for Executor, ExecutorService, ScheduledExecutorService, ThreadFactory, and Callable classes.
* Executors class can be used to easily create Thread Pool in java, also this is the only class supporting execution of Callable implementations.

# What are some of the improvements in Concurrency API in Java 8?
Some important concurrent API enhancements are:
- ConcurrentHashMap compute(), forEach(), forEachEntry(), forEachKey(), forEachValue(), merge(), reduce() and search() methods.
- CompletableFuture that may be explicitly completed (setting its value and status).
- Executors newWorkStealingPool() method to create a work-stealing thread pool using all available processors as its target parallelism level.

# Differences between concurrency vs. parallelism?
In Short,
- Concurrency means multiple tasks which start, run, and complete in overlapping time periods, in no specific order. Parallelism is when multiple tasks OR several part of a unique task literally run at the same time, e.g. on a multi-core processor.
- Remember that Concurrency and parallelism are NOT the same thing.

**Differences between concurrency vs. parallelism**
- Now let’s list down remarkable differences between concurrency and parallelism.
- Concurrency is when two tasks can start, run, and complete in overlapping time periods. Parallelism is when tasks literally run at the same time, eg. on a multi-core processor.
- Concurrency is the composition of independently executing processes, while parallelism is the simultaneous execution of (possibly related) computations.
- Concurrency is about dealing with lots of things at once. Parallelism is about doing lots of things at once.
- An application can be concurrent – but not parallel, which means that it processes more than one task at the same time, but no two tasks are executing at same time instant.
- An application can be parallel – but not concurrent, which means that it processes multiple sub-tasks of a task in multi-core CPU at same time.
- An application can be neither parallel – nor concurrent, which means that it processes all tasks one at a time, sequentially.
- An application can be both parallel – and concurrent, which means that it processes multiple tasks concurrently in multi-core CPU at same time.
