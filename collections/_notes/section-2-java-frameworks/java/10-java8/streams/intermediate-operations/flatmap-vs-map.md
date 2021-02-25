---
layout: post
title: flatMap() vs map() 
permalink: /:collection/java/java8/streams/operations/flatmap-vs-map
---


|map	|flatmap|
|---|---|
|used for transformation only	|used for both transformation and flattening|
|returns Optional\<String> for string Stream map function	|returns String type for string Stream map function|
| |After mapping, unwrap to retrieve value|
|Function in map() returns a single value	|function returns a stream of values|
|applies a function on each element of stream and stores the value returned by the function into a new Stream.	|flatMap “flattens” the Stream of Stream of values into Stream of values. (list of the list, can convert it to a big list.)|

```java
Map<String, List<String>> people = new HashMap<>();
people.put("John", Arrays.asList("555-1123", "555-3389"));
people.put("Mary", Arrays.asList("555-2243", "555-5264"));
people.put("Steve", Arrays.asList("555-6654", "555-3242"));
List<String> phones = people.values().stream().flatMap(Collection::stream).collect(Collectors.toList());
```
