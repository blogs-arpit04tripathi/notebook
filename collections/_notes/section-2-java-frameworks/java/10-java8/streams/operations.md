---
layout: post
title: Stream Operations
permalink: /:collection/java/java8/streams/operations
---


* Stream operations can either be executed sequential or parallel.

![intermediate-operations]({{site.cdn}}/java/java8/intermediate-operations.png)
![stream-operations]({{site.cdn}}/java/java8/stream-operations.png)

|Intermediate Operations	| Terminal Operations|
---|---
Return Stream itself, you can do chaining.|return a result of a certain type
Lazy, not executed until a result of a processing is needed.|Eager, traversal of the Stream doesn’t begin until the terminal operation of the pipeline is executed.
filter(), map(), flatMap(), distinct(), sorted(), peek(), limit(), skip()|forEach(), forEachOrdered(), toArray(), reduce(), collect(), min(), max(), count(), anyMatch(), allMatch(), noneMatch(), findFirst(), findAny()

```java
List<Integer> list = Arrays.asList(4, 0, 6, 2); 
boolean answer = list.stream().noneMatch(num -> num < 0);
```
