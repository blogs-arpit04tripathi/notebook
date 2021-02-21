---
layout: post
title: OutOfMemoryError
permalink: /:collection/java/out-of-memory-error
---

- TOC
{:toc}

<hr><br>


# Have you faced OutOfMemoryError in Java? How did you solved that?
- Allowed limit of memory for java application is specified during application startup.
- Heap space and Permgen (for Permanent Generation)
- subclass of java.lang.VirtualMachineError and JVM throws java.lang.OutOfMemoryError when it ran out of memory in heap.
- Two Types of OutOfMemoryError in Java:
	- **Java.lang.OutOfMemoryError**: Java heap space : export JVM_ARGS="-Xms1024m -Xmx1024m"
	- **Java.lang.OutOfMemoryError**: PermGen space : export JVM_ARGS="-XX:PermSize=64M -XX:MaxPermSize=256m"
 
Now, Perm Gen is not there and moved to heap as metaSpace so no more option 2.

![outOfMemoryError]({{site.cdn}}/java/jvm-architecture/outOfMemoryError.png)

# Long Term Solution: 
- Short Term Solution
	- Increasing the Start/Max Heap size
	- changing Garbage Collection options.
	- increased Java heap space also increase the length of [GC pauses](https://plumbr.io/handbook/gc-tuning/example/tuning-for-throughput) affecting your application’s [throughput or latency](https://plumbr.io/handbook/gc-tuning/throughput-vs-latency-vs-capacity).
- Best approach
	- Understand the memory needs of your program 
	- ensure memory is used wisely and does not have leaks. 
- You can use a Java memory profiler to determine what methods in your program are allocating large number of objects and then determine if there is a way to make sure they are no longer referenced, or to not allocate them in the first place.

# What is causing it?
- The application just requires more Java heap space than available to it to operate normally.
- **Memory Footprint** – Runtime memory requirements.
- **Spikes in usage/data volume**: Application recieves spikes of volume of data beyond expected threshold it is designed to handle.
- **Memory leaks**: A particular type of programming error will lead your application to constantly consume more memory. Every time the leaking functionality of the application is used it leaves some objects behind into the Java heap space. 

# Example of memory leak
below code does not contain a proper equals() implementation next to its hashCode() hence causes continuous creation of new objects for Key.
```java
public static void main(String[] args) {
    Map m = new HashMap();
    while (true)
        for (int i = 0; i < 10000; i++)
            if (!m.containsKey(new Key(i)))
              m.put(new Key(i), "Number:" + i);
}
```
```java
@Override
public boolean equals(Object o) {
   boolean response = false;
   if (o instanceof Key) {
      response = (((Key)o).id).equals(this.id);
   }
   return response;
}
```
To solve, you need to figure out which part of your code is responsible for allocating the most memory.
1. Which objects occupy large portions of heap
2. Where these objects are being allocated in source code

Process outline that will help you answer the above questions:
- Get security clearance in order to perform a heap dump from your JVM. 
- “Dumps” are basically snapshot of heap contents that you can analyze. 
- These snapshots can thus contain confidential information, such as passwords, credit card numbers etc, so acquiring such a dump might not even be possible for security reasons.
- Get the dump at the right moment. Be prepared to get a few dumps, as when taken at a wrong time, heap dumps contain a significant amount of noise and can be practically useless. On the other hand, every heap dump “freezes” the JVM entirely, so don’t take too many of them or your end users start facing performance issues.
- Find a machine that can load the dump. When your JVM-to-troubleshoot uses for example 8GB of heap, you need a machine with more than 8GB to be able to analyze heap contents. 
- Fire up dump analysis software.
- Detect the paths to GC roots of the biggest consumers of heap. 
- Next, you need to figure out where in your source code the potentially hazardous large number of objects is being allocated. If you have good knowledge of your application’s source code, you’ll be able to do this in a couple searches.
