---
layout: post
title: When to use Volatile
permalink: /:collection/java/multithreading/when-to-use-volatile
---


* You can use Volatile variable if you want to read and write long and double variable atomically. long and double both are 64 bit data type and by default writing of long and double is not atomic and platform dependence. Many platform perform write in long and double variable 2 step, writing 32 bit in each step, due to this its possible for a Thread to see 32 bit from two different write. You can avoid this issue by making long and double variable volatile in Java.
* volatile variable can be used to inform the compiler that a particular field is subject to be accessed by multiple threads, which will prevent the compiler from doing any reordering or any kind of optimization which is not desirable in a multi-threaded environment. Without volatile variable compiler can re-order the code, free to cache value of volatile variable instead of always reading from main memory. like following example without volatile variable may result in an infinite loop without the volatile modifier, it's not guaranteed that one Thread sees the updated value of isActive from other thread. The compiler is also free to cache value of isActive instead of reading it from main memory in every iteration. By making isActive a volatile variable you avoid these issues.

```java
private boolean isActive = true;
public void printMessage() {
    while (isActive)
        System.out.println("Thread is Active");
}
```

* Another place where a volatile variable can be used is to fixing double-checked locking in Singleton pattern. As we discussed in [Why should you use Enum as Singleton](https://javarevisited.blogspot.com/2012/07/why-enum-singleton-are-better-in-java.html) that double checked locking was broken in Java 1.4 environment.
