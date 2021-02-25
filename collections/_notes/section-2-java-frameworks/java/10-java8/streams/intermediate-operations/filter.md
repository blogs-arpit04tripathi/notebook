---
layout: post
title: filter()
permalink: /:collection/java/java8/streams/operations/filter
---

to filter elements which satisfy a certain condition.

```java
numbers.stream().filter(e -> e%2==0).forEach(e -> System.out.println(e));
```
