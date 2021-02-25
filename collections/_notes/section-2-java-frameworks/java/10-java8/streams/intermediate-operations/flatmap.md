---
layout: post
title: flatmap()
permalink: /:collection/java/java8/streams/operations/flatmap
---

* extension of the map function. Apart from transforming one object into another, it can also flatten it.
* transform each element into zero or more elements by a way of another stream.
* For example, if you have a list of the list but you want to combine all elements of lists into just one list. In this case, you can use flatMap() for flattening. At the same time, you can also transform an object like you do use map() function.

```java
long uniqueWords = java.nio.file.Files.lines(Paths.get(file.toURI()), Charset.defaultCharset())
                    .flatMap(line -> Arrays.stream(line.split(" .")))
                    .distinct()
                    .count();
```
