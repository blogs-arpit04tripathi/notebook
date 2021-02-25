---
layout: post
title: Merging Streams
permalink: /:collection/java/java8/streams/merging-streams
---


```java
Stream<Integer> stream1 = Stream.of(1, 3, 5);
Stream<Integer> stream2 = Stream.of(2, 4, 6);
Stream<Integer> resultingStream = Stream.concat(stream1, stream2);
```
