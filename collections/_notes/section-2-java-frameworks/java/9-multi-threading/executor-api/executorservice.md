---
layout: post
title: ExecutorService
permalink: /:collection/java/multithreading/executorservice
---


- The executor service interface is of course a subinterface of the executor. 
- Responsible for managing the lifecycle of all individual threads, and also of the executor.
- Added method - **submit(Callable)**

|Methods||
---|---
shutdown() | all submitted commands will be executed before stopping the ExecutorService, but no new command is accepted.<br>Doesn’t guarantee that all the task will reach their completion point.<br>shutdown();
shutdownNow()| prevents waiting tasks to be executed and try to stop all currently executing commands and returns List<Runnable> for that were awaiting execution.
awaitTermination()| blocks until all tasks are completed after the shutdown request/time elapses. Current thread is interrupted.<br>awaitTermination(5, TimeUnit.SECONDS);
<T> List<Future<T>> invokeAll(Collection<? extends Callable<T>> tasks)| submits all tasks and executes all.
<T> T invokeAny(Collection<? extends Callable<T>> tasks)|submits all tasks and executes some tasks and as soon as gets first successful response, it cancels rest of the tasks.<br>invokeAny may be used for certain **use cases** where let's say you want a guaranteed delivery system to be implemented okay? You want to send messages and you can post the message as many number of times as you want, but you want an assurance that it definitely gets delivered at least once. (for idempotent operations)

```java
Future<String> resultFromMyCommand2 = executorService.submit(myCommand2);
executorService.shutdown();
// Will throw a RejectedExecutionException because no new task can be submitted
executorService.submit(myCommand3);
```
