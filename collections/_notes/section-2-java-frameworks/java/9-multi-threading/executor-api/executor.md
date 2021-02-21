---
layout: post
title: Executor
permalink: /:collection/java/multithreading/executor
---


- execute(Runnable)
- To create an Executor it is possible to use the factory Executors class.
- **newSingleThreadExecutor** - an ExecutorService with a single thread to execute commands.
	
	```java
	// Creates a single thread ExecutorService
	ExecutorService singleExecutorService = Executors.newSingleThreadExecutor();
	```

- **newSingleThreadScheduledExecutor** - a ScheduledExecutorService with a single thread to execute commands.
	
	```java
	// Creates a single thread ScheduledExecutorService
	ScheduledExecutorService singleScheduledExecutorService = Executors.newSingleThreadScheduledExecutor();
	```

- **newFixedThreadPool** - an ExecutorService that use a fixed length pool of threads to execute commands.
	
	```java
	// Creates an ExecutorService that use a pool of 10 threads
	ExecutorService fixedExecutorService = Executors.newFixedThreadPool(10);
	```

- **newScheduledThreadPool** - a ScheduledExecutorService with a fixed length pool of threads to execute scheduled commands.
	
	```java
	// Creates a ScheduledExecutorService that use a pool of 5 threads
	ScheduledExecutorService fixedScheduledExecutorService = Executors.newScheduledThreadPool(5);
	```

- **newCachedThreadPool** - an ExecutorService with a pool of threads that creates a new thread if no thread is available and reuse an existing thread if they are available. Expandable pool.
	
	```java
	// Creates an ExecutorService that use a pool that creates threads on demand And that kill them after 60 seconds if they are not used
	ExecutorService onDemandExecutorService = Executors.newCachedThreadPool();
	```

- **newWorkStealingPool**(parallelism) – fork and join inplementation
