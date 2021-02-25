---
layout: post
title: forEach()
permalink: /:collection/java/java8/streams/operations/forEach
---

* for iterating over all elements of a stream and perform some operation on each of them.

```java
listPersons.stream().filter(p -> p.getGender().equals(Gender.FEMALE)).forEach(System.out::println);
```
