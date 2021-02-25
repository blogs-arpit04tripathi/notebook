---
layout: post
title: Primitive Type Streams
permalink: /:collection/java/java8/streams/primitive
---


* Streams primarily work with collections of objects and not primitive types.
* IntStream, LongStream, and DoubleStream.
* Primitive streams are limited mainly because of boxing overhead and because creating specialized streams for other primitives isn’t’ that useful in many cases.

```java
int[] integers = new int[] {20, 98, 12, 7, 35};
int min = Arrays.stream(integers).min().getAsInt();  // returns 7
double avg = IntStream.of(20, 98, 12, 7, 35).average().getAsDouble(); // returns 34.4
int sum = IntStream.range(1, 10).sum();       // returns 45
int sum = IntStream.rangeClosed(1, 10).sum(); // returns 55    last element included
IntStream.rangeClosed(1, 5).parallel().forEach(System.out::println);
```

* As helpful as these fancy loops are, it’s still better to use the traditional for-loops instead of the functional one for simple iterations because of simplicity, readability, and performance in some cases.

```java
Arrays.stream(integers).asDoubleStream().forEach(e->System.out.print(e + " "));
Arrays.stream(integers).asLongStream().forEach(e->System.out.print(e + " "));
```
