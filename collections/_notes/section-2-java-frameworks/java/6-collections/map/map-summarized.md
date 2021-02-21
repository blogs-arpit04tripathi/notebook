---
layout: post
title: Maps Summarized
permalink: /:collection/java/collections/map-summarized
---

|Property|HashMap|TreeMap|LinkedHashMap|HashTable|
|---|---|---|---|---|
|Insertion Order	|Random	|Sorted (Natural Order)			|Sorted (Insertion Order)	|Random	|
|Performance		|O(1)	|O(log(n))						|O(1)						|O(1)	|
|Null Keys			|Yes	|No								|Yes						|No		|
|Null Values		|Yes	|No								|Yes						|No		|
|Interfaces			|Map	|Map, SortedMap, NavigableMap	|Map						|Map	|
|Synchronized		|No, `Collections.synchronizedMap(new HashMap())`|||Yes|
|Implementation Algorithm|Buckets|Red-Black Tree			|HashTable and LinkedList using doubly linked list of Buckets|Buckets|
|Comments			|Efficient|Extra Cost of Maintaining TreeMap|TreeMap Advantages, no extra cost|Obselete|
