---
layout: post
title: Executor API
permalink: /:collection/java/multithreading/executor-api
---


* The Executor framework is a framework for standardizing invocation, scheduling, execution, and control of asynchronous tasks according to a set of execution policies.
* Creating a lot many threads with no bounds to the maximum threshold can cause application to run out of heap memory. So, creating a ThreadPool is a better solution as a finite number of threads can be pooled and reused. Executors framework facilitate process of creating Thread pools in java.

![threadpool]({{site.cdn}}/java/multi-threading/threadpool.png)

![executor-service]({{site.cdn}}/java/multi-threading/executor-service.png)

# Java Thread Pool

* Java Thread pool represents a fixed-size group of worker threads that are waiting for the job and reused many times.
* It contains a queue that keeps tasks(Runnable Threads) waiting to get executed.
* A thread from the thread pool is pulled out and assigned a job by the ExecutorService. After completion of the job, thread is contained in the thread pool again.

**Advantage**
- Better performance. It saves time because there is no need to create new thread.

**Real time usage**
- Used in Servlet and JSP where container creates a thread pool to process the request.

**How can we create Thread Pool in Java?**  
Executors factory methos can be used to create ThreadPool in java.
 
* The [Reactor pattern](https://en.wikipedia.org/wiki/Reactor_pattern) is used with worker threads to overcome a common scenario in applications: You need to do a lot of work eventually but you don't know which work and when and creating threads is an expensive operation.
* The idea is that you create a lot of threads which don't do anything at first. Instead, they "wait for work". When work arrives (in the form of code), some kind of executor service (the reactor) identifies idle threads from the pool and assigns them work to do.
* That way, you can pay the price to create all the threads once (and not every time some work has to be done). At the same time, your threads are generic; they will do whatever work is assigned to them instead of being specialized to do something specific.
