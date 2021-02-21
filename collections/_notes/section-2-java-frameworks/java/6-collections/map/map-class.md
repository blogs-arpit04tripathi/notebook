---
layout: post
title: Map Classes
permalink: /:collection/java/collections/map-class
---

|Class|Description|
|---|---|
|AbstractMap |Implements most of the Map interface.|
|HashMap 			|Extends AbstractMap to use a hash table.|
|LinkedHashMap 		|Extends HashMap to allow insertion-order iterations.|
|TreeMap 			|Extends AbstractMap to use a tree.			|
|EnumMap 			|Extends AbstractMap for use with enum keys.|
|WeakHashMap 		|Extends AbstractMap to use a hash table with weak keys.|
|IdentityHashMap	|Extends AbstractMap and uses reference equality when comparing documents.|

**Arrange the following in the ascending order (performance)?**  
Hashtable < Collections.SynchronizedMap < ConcurrentHashMap < HashMap

# hashcode() and equals()

**hashCode() and equals() methods, what is their contract?**  
* hashCode() and equals() of key object is critical. 
* Implementation of equals() and hashCode() should follow these rules:
	- `o1.equals(o2)` true => `o1.hashCode() == o2.hashCode()` always true.
	- `o1.hashCode() == o2.hashCode()` true => not necessary that `o1.equals(o2)` is true.

**What are use-cases of hashcode() and equals()?**  
* HashMap – uses hashcode() of Key object to determine index of segment where key-value pair is to be put. 
* HashMap – uses hashcode() to find lookup segement index, then equals() to get value from linked list in segment. 
* Collection classes that doesn’t allow duplicates uses hashCode() and equals() to find duplicates. Ex- HashSet.

**Can we use any class as Map key?**  
* Only if hashCode and equals contract is maintainted. 
* If class overrides equals(), should override hashCode() too.
* Only those fields used in equals() should be used in hashCode().
* Best practice - user defined key class to be made immutable, so that hashCode() value can be cached for fast performance.
* Immutable classes makes sure that hashCode() and equals() will not change in future as well.

**What is problem if hashcode and equals not correctly implemented?**  
two different Key’s might produce same hashCode() and equals(), causing faulty overwriting of element in HashMap.

**Why have immutable objects as keys? Or Where do we need immutable Objects?**  
* Due to possibility of below case, immutable classes are used as keys such as String, Integer etc.

```java
MyKey key = new MyKey("Pankaj");        // assume hashCode=1234
myHashMap.put(key, "Value");
key.setName("Amit");                    // assume new hashCode=7890
myHashMap.get(new MyKey("Pankaj"));     // not found
```

**What is hash-collision in Hashtable ? How it was handled in Java?**  
* In Hashtable, if two different keys have the same hash value then it leads to hash-collision. 
* A bucket of type linkedlist used to hold the different keys of same hash value.