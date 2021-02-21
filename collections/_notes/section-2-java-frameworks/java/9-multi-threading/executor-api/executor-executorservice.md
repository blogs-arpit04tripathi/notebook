---
layout: post
title: Executor and ExecutorService
permalink: /:collection/java/multithreading/executor-executorservice
---


- The ***Executor framework*** helps to **decouple a command submission from command execution**.
- In the java.util.concurrent package there are three interfaces:
	- **Executor**- Used to submit a new task.
	- **ExecutorService**- subUnterface that adds methods to manage lifecycle of threads used to run the submitted tasks and methods to produce a Future to get a result from an asynchronous computation.
	- **ScheduledExecutorService**- to execute commands periodically or after a given delay.

![executor-service-internal]({{site.cdn}}/java/multi-threading/executor-service-internal.png)

```java
Thread t = new Thread(new MyRunnable());
t.start();
```
```java
Executor executor = ... // Executor creation
executor.execute(new MyRunnable());
executorService.submit(callable);
```
