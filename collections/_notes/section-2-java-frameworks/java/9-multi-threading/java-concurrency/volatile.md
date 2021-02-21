---
layout: post
title: volatile Keyword
permalink: /:collection/java/multithreading/volatile
---


* Using volatile is yet another way (like synchronized, atomic wrapper) of making class thread safe.
* volatile is used to indicate that a **variable's value will be modified by different threads**.
* Declaring a volatile Java variable means:
  - The value of this variable will ***never be cached thread-locally***: all reads and writes will go straight to "main memory";
  - Access to the variable ***acts as though it is enclosed in a synchronized block***, synchronized on itself.

```java
class SharedObj {
    // Changes made to sharedVar in one thread may not immediately reflect in other thread
    static int sharedVar = 6;
    // static volatile int sharedVar = 6;
}
```

* Suppose that two threads are working on **SharedObj**. If two threads run on different processors each thread may have its own local copy of **sharedVar**.
* If one thread modifies its value the change might not reflect in the original one in the main memory instantly. This depends on the [write policy](https://en.wikipedia.org/wiki/CPU_cache#Write_policies) of cache. Now the other thread is not aware of the modified value which leads to data inconsistency.

![volatile]({{site.cdn}}/java/multi-threading/volatile.png)

# Write Policy
* The timing of writing data from cache to main memory is known as the **write policy**.
  - [write-through](https://en.wikipedia.org/wiki/Cache_(computing)#WRITE-THROUGH) cache, every write to the cache causes a write to main memory.
  - [write-back](https://en.wikipedia.org/wiki/Cache_(computing)#WRITE-BACK) or **copy-back cache**, writes are not immediately mirrored to the main memory, and the cache instead tracks which locations have been written over, marking them as [dirty](https://en.wikipedia.org/wiki/Dirty_bit).
* Note that write of normal variables without any synchronization actions, might not be visible to any reading thread (this behavior is called [sequential consistency](https://en.wikipedia.org/wiki/Sequential_consistency)). 
*	Have only one copy of static variables in main memory. 
