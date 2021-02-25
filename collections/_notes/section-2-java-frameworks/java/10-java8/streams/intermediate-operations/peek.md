---
layout: post
title: peek()
permalink: /:collection/java/java8/streams/operations/peek
---

* used for debugging the issues related to lambda expression and Stream processing.
* can peek through each step and print meaningful messages on the console.
* *peek()* expects a *Consumer<T>* as its only argument
* the snippet below produces no output as peek is an intermediate operation.

```java
Stream<String> nameStream = Stream.of("Alice", "Bob", "Chuck");
nameStream.peek(System.out::println);

Stream.of("one", "two", "three", "four").filter(e -> e.length() > 3)
      .peek(e -> System.out.println("Filtered value: " + e))
      .map(String::toUpperCase)
      .peek(e -> System.out.println("Mapped value: " + e))
      .collect(Collectors.toList());
```
Alternatively, we could have used map(), but peek() is more convenient since we don’t want to replace the element.
