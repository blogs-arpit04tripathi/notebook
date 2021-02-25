---
layout: post
title: sorted()
permalink: /:collection/java/java8/streams/operations/sorted
---

returns a sorted view of the stream, elements are sorted in natural order unless you pass a custom Comparator.

```java
numbers.stream().sorted().forEach(e -> System.out.println(e));
```
