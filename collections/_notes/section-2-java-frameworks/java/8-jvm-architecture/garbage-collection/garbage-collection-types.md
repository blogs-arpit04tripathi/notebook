---
layout: post
title: Garbage Collection Types
permalink: /:collection/java/garbage-collection-types
---

- Use JVM switch to enable the garbage collection strategy for the application.
- 5 types of garbage collection.
- **Serial GC (-XX:+UseSerialGC)**
  - simple **mark-sweep-compact** approach for young and old generations garbage collection i.e Minor and Major GC. 
  - It is good for small applications with low memory footprint.
  - useful in client-machines
    - simple stand-alone applications
    - machines with smaller CPU. 
- **Parallel GC (-XX:+UseParallelGC)**
  - Also called **throughput collector** because it uses multiple CPUs to speed up the GC performance. 
  - Same as Serial GC except that is **spawns N threads for young generation garbage collection**
    - **N is the number of CPU cores** in the system. 
  - Parallel GC uses **single thread for Old Generation** garbage collection.
  - We can control the number of threads using `-XX:ParallelGCThreads=n` JVM option.
- **Parallel Old GC (-XX:+UseParallelOldGC)**
  - same as Parallel GC, uses multiple threads for both Young Generation and Old Generation garbage collection.
- **Concurrent Mark Sweep (CMS) Collector (-XX:+UseConcMarkSweepGC)**
  - known as **concurrent low pause collector**. 
  - does the garbage collection for Old generation.
  - CMS collector tries to minimize the pauses due to garbage collection.
    - by doing most of the garbage collection work concurrently with the application threads.
  - CMS collector on young generation uses the same algorithm as that of the parallel GC.
  - Suitable for responsive applications where we can’t afford longer pause times. 
  - Can limit the number of threads in CMS collector using `-XX:ParallelCMSThreads=n` JVM option.
- **G1 Garbage Collector (-XX:+UseG1GC)**
  - Garbage First or G1 garbage collector
  - it’s long term goal is to replace the CMS collector.
  - parallel, concurrent, and incrementally compacting low-pause garbage collector.
  - G1 GC doesn’t work like other collectors and there is no concept of Young and Old generation space.
  - It divides the heap space into multiple equal-sized heap regions.
  - When a garbage collection is invoked, it first collects the region with lesser live data, hence “Garbage First”.
