---
layout: post
title: Parallel Stream
permalink: /:collection/java/java8/streams/parallel-streams
---


**What is the parallel Stream? How can you get a parallel stream from a List?**  
* A parallel stream can parallely execute stream processing task. 
* When a stream executes in parallel, the Java runtime partitions the stream into multiple sub-streams.
* parallelStream() can parallelize execution but there is significant overhead or parallelism which only pays off if you are doing bulk data operation.
* example, filter order worth more than 1 lacs in a parallel stream of 1 million orders.
* Unlike sequential Stream, the parallel stream can launch multiple threads to search for those orders on the different part of Stream and then combine the result.
* Collection.stream() and Collection.parallelStream()
* Read more about parallel stream [here](https://netjs.blogspot.com/2017/01/parallel-stream-in-java-stream-api.html).

**What is the benefit of using parallel stream?**  
* When parallel stream is used the Java runtime partitions the stream into multiple sub-streams. 
* This parallel execution of data, with each sub-stream running in a separate thread, will result in increase in performance.
