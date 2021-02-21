---
layout: post
title: Spliterators
permalink: /:collection/java/collections/split-iterator
---

* supports parallel programming, ability to parallel iteration of portions of the sequence.
* combines hasNext and next into one method `tryAdvance()`, streamlined approach.

### Basic iteration task is quite easy:
* tryAdvance( ) until it returns **false**.
* For **tryAdvance( )**, each iteration passes next element to objRef. Often, implementing **Consumer** by lambda is easiest way.
* **forEachRemaining()**, streamlined alternative, **Consumer** defines action. 

**Spliterator**
* most useful for parallel processing.
* attributes, called characteristics are static *int*. 
	- example - SORTED, DISTINCT, SIZED, and IMMUTABLE, etc.
* Spliterator.OfPrimitive(), Spliterator.OfDouble, Spliterator.OfInt, and Spliterator.OfLong.

```java
ArrayList<Double> vals;
Spliterator<Double> spltitr = vals.spliterator();
while(spltitr.tryAdvance((n) -> System.out.println(n)));
System.out.println();
spltitr = vals.spliterator();
ArrayList<Double> sqrs = new ArrayList<>();
while(spltitr.tryAdvance((n) -> sqrs.add(Math.sqrt(n))));
System.out.print("Contents of sqrs:\n");
spltitr = sqrs.spliterator();
spltitr.forEachRemaining((n) -> System.out.println(n));

// Contents of vals:
1.0
2.0
3.0
4.0
5.0

// Contents of sqrs:
1.0
1.4142135623730951
1.7320508075688772
2.0
2.23606797749979
```