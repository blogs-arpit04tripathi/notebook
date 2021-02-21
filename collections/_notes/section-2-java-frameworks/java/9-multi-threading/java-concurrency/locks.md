---
layout: post
title: Locks
permalink: /:collection/java/multithreading/locks
---


* One of the ways to manage access to an object is to use locks by using the synchronized keyword.
* The synchronized keyword ensures that only one thread can enter the method at one time.
* Additionally, we need to add the volatile keyword to ensure proper reference visibility among threads.

# Using locks solves the problem. However, performance takes a hit.
* When multiple threads attempt to acquire a lock, one of them wins, while the rest of the threads are either blocked or suspended. The process of suspending and then resuming a thread is very expensive and affects the overall efficiency of the system.
* In a small program, such as the counter, the time spent in context switching may become much more than actual code execution, thus greatly reducing overall efficiency.

```java
import java.util.concurrent.atomic.AtomicInteger;
class AtomicCounter {
    private AtomicInteger c = new AtomicInteger(0);
    public void increment() {
        c.incrementAndGet();
    }
    public void decrement() {
        c.decrementAndGet();
    }
    public int value() {
        return c.get();
    }
}
```
```java
AtomicBoolean
AtomicInteger
AtomicIntegerArray
AtomicIntegerFieldUpdater
AtomicLong
AtomicLongArray
AtomicLongFieldUpdater
AtomicReference
LongAdder
```
