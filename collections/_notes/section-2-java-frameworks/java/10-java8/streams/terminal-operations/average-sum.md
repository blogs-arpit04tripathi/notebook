---
layout: post
title: average() and sum()
permalink: /java8/streams/operations/average-sum
---

```java
Arrays.stream(array).mapToInt(Integer::intValue).sum();
Arrays.stream(array).average().orElse(Double.NaN);
```