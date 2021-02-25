---
layout: post
title: collect()
permalink: /:collection/java/java8/streams/operations/collect
---

collect() method used to receive elements from a stream and store them in a collection and mentioned in parameter function.
```java
numbers.parallelStream().filter(e -> e%2 ==0).mapToInt(e -> e *2).collect(Collectors.toList());
List<String> listEmails = listPersons.stream().map(p -> p.getEmail()).collect(Collectors.toList());
Set<String> setEmails = listPersons.stream().map(p -> p.getEmail()).collect(Collectors.toCollection(TreeSet::new));
Map<Gender, List<Person>> byGender = listPersons.stream().collect(Collectors.groupingBy(p -> p.getGender()));
// output
{
  FEMALE=[Alice Brown, Carol Hill, Isabell Hill, Jane Smith], 
  MALE=[Bob Young, David Green, Gibb Brown, Henry Baker]
}

String firstNames = listPersons.stream().map(p -> p.getFirstName()).collect(Collectors.joining(", "));   // Alice, Bob, Carol, David
```

number of products being sold for each currency
```java
Map<String, Integer> totalProductByCurrency = 
pList.stream().collect(Collectors.groupingBy(Product::getCurrency, Collectors.reducing(0, 1L, Integer::sum)));
```
	
sum of all the product quantity grouped by currency
```java
Map<String, Integer> totalProductByCurrency = 
pList.stream().collect(Collectors.groupingBy(Product::getCurrency, Collectors.reducing(0, Product.getQuantity(), Integer::sum)));
```
	
average of the product quantity based on Currency
```java
Map<String, Integer> totalProductByCurrency = 
pList.stream().collect(Collectors.groupingBy(Product::getCurrency, Collectors.averagingInt(Product::getQuantity)));
```