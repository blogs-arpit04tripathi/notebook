---
layout: post
title: atomic variables
permalink: /:collection/java/multithreading/atomic
---


* The java.util.concurrent.atomic package defines classes that support atomic operations on single variables.
* All classes have get and set methods that work like reads and writes on volatile variables. 
* set has a happens-before relationship with any subsequent get on the same variable.
* The atomic ***compareAndSet*** method also has these memory consistency features, as do the simple atomic arithmetic methods that apply to integer atomic variables.
* In below example, If two threads try to get and update the value at the same time, it may result in lost updates.

```java
class Counter {
    private int c = 0;
    public void increment() {
        c++;
    }
    public void decrement() {
        c--;
    }
    public int value() {
        return c;
    }
}
```
```java
class SynchronizedCounter {
    private int c = 0;
    public synchronized void increment() {
        c++;
    }
    public synchronized void decrement() {
        c--;
    }
    public synchronized int value() {
        return c;
    }
}
```
* For this simple class, synchronization is an acceptable solution.
* For a more complicated class, we can use atomic wrappers/classes. Example, replace int with ***AtomicInteger***.
