---
layout: post
title: Strings
permalink: /:collection/java/strings
---

* String in java is an **object rather than character arrays**. (sequence of characters) 
* String is **immutable**, cannot change characters once created. 
* Each modification creates a new **String** object, original left unchanged.   (s = s + “xyz”;)
	- **Reason**: because fixed, immutable strings can be implemented more efficiently than changeable ones. 
* **StringBuffer and StringBuilder** – **modifiable (mutable)**
* String, StringBuffer, StringBuilder - **final class** and implement the **CharSequence interface**.
* implements **Comparable\<T>** interface, method **compareTo()** for sorting.

```java
String s = "This is a demo of the getChars method.";        // string literal
int start = 10; int end = 14; char buf[] = new char[end - start];
s.getChars(start, end, buf, 0);   // getBytes(String) throws UnsupportedEncodingException
System.out.println(buf);    => returns demo
```
* concatenation - for creating very long strings. 
* Convert data into string representation by overloaded **valueOf()**.

|Overloaded valueOf()||
|---|---|
|primitive types | valueOf() returns a string in human-readable value.
|objects | valueOf() calls the toString( ). 
|array | valueOf() returns cryptic string, indicating that its an array of some type. 

* For arrays of char, String object is created that contains the characters in the char array.
* Most Internet protocols and text file formats use 8-bit ASCII for all text interchange, **getBytes()** is used here.
* **equals()** for characters,== for references.
  * `==` true implies `.equals` is also true but not vice-versa.

```java
String s1 = "Hello";
String s2 = new String(s1); // .equals is true but == is false
```
