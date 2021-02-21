---
layout: post
title: Iterator
permalink: /:collection/java/collections/iterator
---

* Iterator - to cycle through a collection, obtaining or removing elements.
* ListIterator - allow bidirectional traversal of a List, and the modification of elements. 
* remove() - ***UnsupportedOperationException*** when used with a read-only collection.
* Java8, can use Spliterator to cycle through a collection. It works differently than does Iterator.

**What is an Iterator?**  
* Iterator interface - provides methods to iterate over any Collection, implements [Iterator Design Pattern](https://www.journaldev.com/1716/iterator-design-pattern-java).
* iterator() method. 
* allows removal during the iteration, doesn’t throw **ConcurrentModificationException**.

**Why there is not method like iterator.add() to add elements to the collection?**  
* Iterator makes no guarantees about the order of iteration.
* ListIterator provide add(), as it guarantees the order of iteration.

**Why Iterator don’t have a method to get next element directly without moving the cursor?**  
* It can be implemented on top of current Iterator interface but since it’s use will be rare; it doesn’t make sense to include it in the interface that everyone has to implement.

**Why there are no concrete implementations of Iterator interface?**  
* Iterator interface declares methods for iterating a collection.
* implementation is responsibility of the Collection implementation classes.
* ***Every collection class has its own Iterator implementation nested class***.
* Collection classes decide whether iterator is fail-fast or fail-safe.

# For-Each Alternative to Iterators
* not modifying while iterating, or reverse order.
* forward direction for any Iterable collection. 

```java
List<String> strList = new ArrayList<>();
for(String obj : strList)		//using for-each loop
    System.out.println(obj);

Iterator<String> it = strList.iterator();
while(it.hasNext()){
    String obj = it.next();
    System.out.println(obj); 
}

ListIterator<String> litr = al.listIterator();
while(litr. hasPrevious()) {
 String element = litr.previous();
 litr.set(element + "+");
}
```

# Why not use for loop for Collections
### For loop
* int i = 0 is an assignment and creation (2 operations)
* i get size, check value of i, and compare (3 operations)
* i++ gets i then adds 1 to it [++i is only 2 operations] this one (3 operations)
* *7/8 operations in total, each time the loop runs through

### Iterator/Enumeration
* while(){} :
* while(v.hasNext()) hasNext true or false (1 operation)
* while(v.hasMoreElements()) hasMore true or false (1 operation)
* Only one operation per repeat of this loop