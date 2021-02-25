---
layout: post
title: Collection Improvements
permalink: /:collection/java/java8/collection-improvements
---

# Array Method Improvements
**What is the new method family introduced in Java 8 for processing of Arrays on multi core machines?**  
* Arrays class methods to use power of multi core machines.
* `Arrays.parallelSetAll()`, `Arrays.parallelSort()` etc.

# Spliterator
> Read more about Spliterator in Java [here](https://netjs.blogspot.com/2017/01/spliterator-in-java.html){:target="_blank"}.

**What is Spliterator in Java SE 8?**  
* Spliterator stands for Splitable Iterator.
* Like Iterator and ListIterator, it is also one of the Iterator interfaces.
* Spliterators, like iterators, are for traversing the elements of a source.
* Spliterator can split the source and iterate the splitted parts in parallel. That way a huge data source can be divided into small sized units that can be traversed and processed parallely.
* You can also use spliterator even if you are not using parallel execution.

**Differences between Iterator and Spliterator in Java SE 8?**  

|	Spliterator	| Iterator |
|---|---
|It is introduced in Java SE 8.|It is available since Java 1.2.|
|Splitable Iterator	|Non-Splitable Iterator|
|It is used in Stream API.	|It is used for Collection API.|
|It uses Internal Iteration concept to iterate Streams.	|It uses External Iteration concept to iterate Collections.|
|We can use Spliterator to iterate Streams in Parallel and Sequential order.	|We can use Iterator to iterate Collections only in Sequential order.|
|We can get Spliterator by calling spliterator() method on Stream Object.	|We can get Iterator by calling iterator() method on Collection Object.|
|Important Method: tryAdvance()	|Important Methods: next(), hasNext()|
