---
layout: post
title: Deamon Thread
permalink: /:collection/java/multithreading/deamon-thread
---


* **Daemon thread** in java is a service provider thread that provides services to the user thread. 
* It is a low priority thread.
* Its life depend on the mercy of user threads i.e. ***when all the user threads dies, JVM terminates this thread automatically***. 
* There are many java daemon threads running automatically e.g. gc, finalizer etc. 
* You can see all the detail by typing the jconsole in the command prompt. The jconsole tool provides information about the loaded classes, memory usage, running threads etc.

|||
---|---
public void setDaemon(boolean status)|used to mark the current thread as daemon thread or user thread.
public boolean isDaemon()|used to check that current is daemon.

* To make a user thread as Daemon, it must not be started otherwise it will throw **IllegalThreadStateException**. 

```java
t1.start();
t1.setDaemon(true);    //will throw exception here  
```
