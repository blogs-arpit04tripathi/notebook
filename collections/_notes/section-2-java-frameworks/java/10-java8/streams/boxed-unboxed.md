---
layout: post
title: Boxed and Unboxed
permalink: /:collection/java/java8/streams/boxed-unboxed
---


```java
List<Integer> evenInts = IntStream.rangeClosed(1, 10).filter(i -> i % 2 == 0).boxed().collect(Collectors.toList());
int sum = Arrays.asList(33,45).stream().mapToInt(i -> i).sum();
```
We can always use ***mapToXxx*** and ***flatMapToXxx*** methods to create primitive streams.

# String to Stream of chars
```java
String testString = “String”;
IntStream intStream = testString.chars();
Stream<Character> characterStream = testString.chars().mapToObj(c -> (char) c);
Stream<Character> characterStream2 = testString.codePoints().mapToObj(c -> (char) c);
Stream<String> stringStream = testString.codePoints().mapToObj(c -> String.valueOf((char) c));
```
* codePoints() - to get an instance of IntStream from a String. 
* Advantage of codepoint - Unicode supplementary characters can be handled effectively.
* Supplementary characters are represented by Unicode surrogate pairs and will be merged into a single codepoint. 

# Iterate over array
```java
// getEvenIndexedStrings
List<String> evenIndexedNames = IntStream.range(0, names.length)
                                  .filter(i -> i % 2 == 0)
                                  .mapToObj(i -> names[i])
                                  .collect(Collectors.toList());
```
