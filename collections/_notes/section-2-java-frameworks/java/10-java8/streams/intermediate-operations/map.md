---
layout: post
title: map()
permalink: /:collection/java/java8/streams/operations/map
---

* transform the elements in a stream of different type using the provided function.

```java
numbers.parallelStream().filter(e -> e%2 ==0).mapToInt(e -> e *2).sum()
Stream.of ("one", null, "three").map(s-> ((s == null) ? "[unknown]" : s)).collect (Collectors.toList ());
```

* Example - List of String to List of Integer, you can use map() to do so.
* Just supply a function to convert String to Integer e.g. parseInt() to map() and it will apply that to all elements of List and give you a List of Integer. In other words, the map can convert one object to other.
