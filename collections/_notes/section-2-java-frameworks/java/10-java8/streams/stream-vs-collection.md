---
layout: post
title: Stream vs Collections
permalink: /:collection/java/java8/stream-vs-collection
---


* source of data - Collection or Arrays. 
* Stream keeps the order of the data as it is in the source.

|COLLECTION API	| STREAM API|
---|---
in-memory data structure to hold values	|doesn't store data, work on a view but elements are actually stored by Collection or array
Collection Object is constructed Eagerly.	|Stream Object is constructed Lazily.
all the values should have been populated before using.	|data structure that is computed on-demand
||operates on the source data structure, produce pipelined data that we can use and perform specific operations.
Changes are reflected on collection	|changes made on Stream not reflect on original collection.
||parallelStream() to take advantage of multiple-cores. This will takes care of all the threading issues which will make our code more robust.
External iterator	|Internal iterator
We can use both Spliterator and Iterator to iterate elements. 	|We can’t use Spliterator or Iterator to iterate elements.
to store limited number of Elements.	|to store either Limited or Infinite Number of Elements.
We can iterate and consume elements from a Collection Object at any number of times.|	We can iterate and consume elements from a Stream Object only once.

# How It Can Be Created?

```java
Stream<Integer> stream = null;
stream = Stream.of(new Integer[]{1,2,3,4,5,6,7,8,9}); // from Array
stream = Stream.of(1,2,3,4,5,6,7,8,9);
stream = arrayList.stream();   // or parallelStream() // from some list
IntStream stream = "12345_abcdefg".chars(); // Using String chars or String tokens
Stream.generate(new Random()::nextInt).limit(5).forEach(System.out::println);    // Stream.generate()    // 5 random int
IntStream.iterate(0, i -> i + 1).limit(5).forEach(System.out::println);        // Stream.iterate()    // 1 to 5
new Random().ints().forEach(System.out::println); // Infinite Stream of integers
```
