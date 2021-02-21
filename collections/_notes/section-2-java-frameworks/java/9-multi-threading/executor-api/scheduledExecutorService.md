---
layout: post
title: ScheduledExecutorService
permalink: /:collection/java/multithreading/scheduledExecutorService
---

- ScheduledExecutorService is used to schedule command executions after a given delay or periodically.
- It must be used as a replacement for Timer and TimerTask.
- Output available in ScheduledFuture Object.

```java
ScheduledExecutorService scheduledExecutorService = Executors.newScheduledThreadPool(5);
// Will start command1 after 50 seconds
scheduledExecutorService.schedule(command1, 50L, TimeUnit.SECONDS);
// Will start command 2 after 20 seconds, 25 seconds, 30 seconds ...
scheduledExecutorService.scheduleAtFixedRate(command2, 20L, 5L, TimeUnit.SECONDS);
// Will start command 3 after 10 seconds and if command3 takes 2 seconds to be executed also after 17, 24, 31, 38 seconds...
scheduledExecutorService.scheduleWithFixedDelay(command3, 10L, 5L, TimeUnit.SECONDS);
```

# Custom Thread Factory
- Implements ThreadFactory
- Overload newThread(Runnable)
- Can be used when you need to have a meaningful thread names for making debugging from Thread dumps.
- Executors.newFixedThreadPool(3, new CustomThreadFactory());

***Use Case***
1. define a user bean to store all user information.
2. DBConnection class.
3. UserDao with method to insert (prepared statement).
4. UserProcessor, callable with userRec as String and Dao. 
5. MainExecutor, read all lines in to list and forEach submit callable.

![custom-thread-factory-usecase]({{site.cdn}}/java/multi-threading/custom-thread-factory-usecase.png)
