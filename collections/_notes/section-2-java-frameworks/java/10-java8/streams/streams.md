---
layout: post
title: Streams
permalink: /:collection/java/java8/streams
---


* Stream - It is an iterator that allows a single run over the collection.
* can use streams to perform functional operations like, filer or map/reduce.
* can run sequentially or parallely.
* Parallel mode makes use of fork/join framework and can leverage power of multiple cores.
* Java stream doesn't store data. It operates on the source data structure and produce pipelined data.
* Streams - Sequence of elements supporting sequencial and parallel aggregate operations.

![]({{site.cdn}}/java/java8/streams.png)

```java
List<Integer> numbers = Arrays.asList(1,2,3,4,5,6,7,8,9,10);
numbers.stream().filter(e -> e%2 ==0).forEach(e -> System.out.println(e));
System.out.println(numbers.stream().filter(e -> e%2 ==0).mapToInt(e -> e *2).sum());
```
If our input is large, we can use parallel stream as well as shown below:
```java
System.out.println(numbers.parallelStream().filter(e -> e%2 ==0).mapToInt(e -> e *2).sum());        // multi-core power
```

**What is stream pipelining in Java 8?**  
* Concept of Pipelining data and chaining operations together.
* Done by splitting operations that can work with streams. (intermediate and terminal operations)
* Each intermediate operation returns an instance of a stream when it runs.
* There must be a terminal operation which will return a final value and will terminate the pipeline.

**What do you mean by saying Stream is lazy?**  
Without terminal operation, stream won’t start processing just because of Stream pipeline.

**When do we go for Java 8 Stream API? Why do we need to use Java 8 Stream API in our projects?**  
When you want to perform the following operations:
* Database like Operations such as groupby, orderby etc.
* perform operations Lazily.
* write Functional Style programming.
* perform Parallel Operations.
* use Internal Iteration
* perform Pipelining operations.
* to achieve better performance, parallelstream().
