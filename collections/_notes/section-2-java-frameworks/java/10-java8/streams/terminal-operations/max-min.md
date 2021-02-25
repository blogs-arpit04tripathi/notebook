---
layout: post
title: max() and min()
permalink: /:collection/java/java8/streams/operations/max-min
---

```java
Optional<Person> min = listPersons.stream().min((p1, p2) -> p1.getAge() - p2.getAge());
Optional<Person> min = listPersons.stream().max((p1, p2) -> p1.getAge() - p2.getAge());
```
