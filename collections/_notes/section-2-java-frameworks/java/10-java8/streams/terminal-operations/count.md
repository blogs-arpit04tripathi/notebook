---
layout: post
title: count()
permalink: /:collection/java/java8/streams/operations/count
---

* Count is a terminal operation returning the number of elements in the stream as a long.

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10,1,2,3,1,1,1);
System.out.print(numbers.stream().filter(e -> e==1).count());
```
