---
layout: post
title: distinct()
permalink: /:collection/java/java8/streams/operations/distinct
---

```java
// int to Integer
List<Integer> distinctIntegers = IntStream.of(5, 6, 6, 6, 3, 2, 2)
                                  .distinct()
                                  .boxed()
                                  .collect(Collectors.toList());
```
