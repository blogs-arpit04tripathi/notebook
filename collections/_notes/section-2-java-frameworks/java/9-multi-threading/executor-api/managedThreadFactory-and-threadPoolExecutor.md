---
layout: post
title: ManagedThreadFactory and ThreadPoolExecutor
permalink: /:collection/java/multithreading/managedThreadFactory-and-threadPoolExecutor
---


- **ManagedThreadFactory** is managed by the container. 
- Like your ManagedExecutorService and your ManagedScheduledExecutorService, this API, too, can be injected using the JNDI lookup or the Resource annotation. 
- ManagedThreadFactory can be used with the Java Standard Edition ExecutorService.
- Inside the Java Standard Edition platform there is an API, called java.util.concurrent.ThreadPoolExecutor which allows you to create and execute a service, specifying your own configuration parameters. 
- **Executors class** provide simple implementation of ExecutorService using **ThreadPoolExecutor** but **ThreadPoolExecutor** provides much more feature than that.
- Let's say for the full size, what is a maximum number of thread that can live in the pool, what is a keeper lifetime, how many tasks should be held in the queue, custom ***RejectedExecutionHandlerImpl*** for tasks when queue is full etc.
- when you create the ExecutorService out of a **ThreadPoolExecutor**, you feed the ManagedThreadFactory API to it so that all the threads manufactured this way will run with the container context.

```java
// Here java.util.concurrent. ExecutorService will have have the entire contextual information of the container
ExecutorService executorService = new ThreadPoolExecutor(10, 15, 2, TimeUnit.SECONDS, new ArrayBlockingQueue(2), managedThreadFactory)
```
- Java provides scheduled thread pool implementation through **ScheduledThreadPoolExecutor class** that implements **ScheduledExecutorService interface**.
