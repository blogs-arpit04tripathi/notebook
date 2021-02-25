---
layout: post
title: Internal and External Iterator
permalink: /:collection/java/java8/internal-external-iterators
---


# External Iterators
* active iterator or explicit iterator. 
* control over iteration is with programmer, define when and how the next element of iteration is called.

# Internal Iterators
* passive iterator, implicit iterator or callback iterator.
* control over iteration of elements lies with the iterator itself, JVM decides the implementation of iteration.
* programmer only tells the iterator "What operation is to be performed on the elements of the collection".
* ***Disadvantage*** – Developer does not get any control over iteration.
* **Usecases**
	- In applications requiring high performance, parallel processing, fast iteration and bulk operations support.
	- other features like parallel processing are important than having control over iteration.

```java
for (String item : items) {System.out.println(item);}    //Traditional java for-each iterator which is an External Iterator.
items.forEach(item -> System.out.println(item));        //Java 8 forEach iterator which is an Internal Iterator.
map.forEach((key,value)->{
	System.out.println(key);
	System.out.println(value);
});
```

**What are the main advantages of Internal Iterator over External Iterator in Java 8?**  
Some of the main advantages of Internal Iterator are:
* Internal Iterator is based on Functional programming; therefore, it can work on declarative style code.
* There is no need to sequentially iterate elements in Internal Iterator.
* Code is more readable and concise.
* supports concurrency and parallel processing.
