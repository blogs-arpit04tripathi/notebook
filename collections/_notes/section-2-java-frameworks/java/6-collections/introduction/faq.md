---
layout: post
title: Collection Frameworks FAQ
permalink: /:collection/java/collections/faq
---

- TOC
{:toc}

<hr><br>

# What is Collection related features in Java 8?
* [Stream API](https://www.journaldev.com/2774/java-8-stream) - sequential and parallel processing
* forEach() - [Iterable interface](https://www.journaldev.com/2389/java-8-features-with-examples#iterable-forEach).
* forEachRemaining(Consumer action), Map replaceAll(), compute(), merge() methods.

# Why Collection interface doesn’t extend Cloneable and Serializable interfaces?
* Collection interface specifies group of Objects known as elements. 
* Actual implementations decide its behaviour, ex. set doesn’t allow duplicate but list does.
* Only implementations decide if they should be cloned or serialized and how.
* So, mandating cloning and serialization in all implementations is actually less flexible and more restrictive.

# What is the root interface in collection hierarchy?
* Root interface in collection hierarchy is Collection interface. 
* Few interviewers may argue that Collection interface extends Iterable interface. So iterable should be the root interface.
  * But you should reply ***iterable interface*** present in `java.lang` package not in java.util package.

# Difference between Collection and Collections?
Collection is an interface while Collections is a java class.

# Why can’t we write code as `List<Number> numbers = new ArrayList<Integer>();`?
* Generics doesn’t support sub-typing because it will cause issues in achieving type safety.
* If Allowed, sample code would have caused **ClassCastException** at runtime while traversing the list of Long.

```java
List<Long> listLong = new ArrayList<Long>();
listLong.add(Long.valueOf(10));
List<Number> listNumbers = listLong; // compiler error
listNumbers.add(Double.valueOf(1.23));
```

# Why can’t we create generic array? or write code as `List<Integer>[] array = new ArrayList<Integer>[10];`?
* arrays are **covariant**, but generics are **invariant**.
* array carry type information of its elements at runtime, this information is used at runtime to throw `ArrayStoreException` if elements type doesn’t match to the defined type. Since generics type information gets erased at runtime by Type Erasure, the array store check would have been passed where it should have failed, hence Generics are invariant.

**Covariant**  
you can assign subclass type array to its superclass array reference.
```java
Object objectArray[] = new Integer[10];     // it will work fine
```

**Invariant**  
cannot assign subclass type generic to its super class generic reference because in generics any two distinct types are neither a subtype nor a supertype.

```java
List<Object> objectList = new ArrayList<Integer>();			// won't compile
List<Integer> arrayOfIntegerList[] = new ArrayList<>[10];	// compile time error !!
```
If Allowed, the below code will throw ClassCastException at runtime.
```java
List<Integer> arrayOfIdList[] = new ArrayList<Integer>[10];	// if generic array creation is legal.
List<String> nameList = new ArrayList<String>();
Object objArray[] = arrayOfIdList;	// that is allowed because arrays are covariant
objArray[0] = nameList;
Integer id = objArray[0].get(0);
```
Here one of the major purposes of generic is failed (i.e., compile time strict type checking). Therefore, to address this problem compile time error gets generated at line 1.