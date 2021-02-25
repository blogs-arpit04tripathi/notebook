---
layout: post
title: reduce()
permalink: /:collection/java/java8/streams/operations/reduce
---

```java
Optional<String> reducedValue = listPersons.stream().map(p -> p.getFirstName()).reduce((name1, name2) -> name1 + ", " + name2);
int sum = Arrays.stream(numbers).reduce(0, (x, y) -> (x + y));
int sum = Arrays.stream(numbers).reduce(0, (x, y) -> (x + y), Integer::sum);
```

```java
U reduce(U identity, BiFunction<U,? super T,U> accumulator, BinaryOperator<U> combiner)
```
* The identity element is both an initial seed value for the reduction and a default result if there are no input elements.
* The accumulator function takes a partial result and the next element, and produces a new partial result
* The combiner function combines two partial results to produce a new partial result (it is necessary in parallel reductions).

# What are Reduction Operations in Java Stream API?
* terminal operations (average, sum, min, max, count) that return one value by combining the contents of a stream.
* called reduction operations because these operations reduce the stream to a single non-stream value.

# What is a mutable reduction operation?
An operation that accumulates input elements into a mutable result container, such as a Collection or StringBuilder.
