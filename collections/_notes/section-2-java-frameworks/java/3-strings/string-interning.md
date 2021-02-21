---
layout: post
title: String Interning
permalink: /:collection/java/strings/string-interning
---


* **intern()** enables == comparision by using pre-existing pool of string literals, faster than equals(). 
* pool of strings -- to save space and faster comparisons.

# Why and When to Intern?
* Java automatically interns all Strings by default. (Literals)
* intern() method with new String() to compare them by == operator.
* ensure that strings having same contents share same memory.

```java
String s1 = "Test";
String s2 = "Test";
String s3 = new String("Test");
final String s4 = s3.intern();
System.out.println(s1 == s2);       // true
System.out.println(s2 == s3);       // false
System.out.println(s3 == s4);       // false
System.out.println(s1 == s4);       // true
System.out.println(s2.equals(s3));  // true
System.out.println(s3.equals(s4));  // true
```

# Memory constraints of using intern()
* internalized strings go to Permanent Generation, reserved for non-user objects, like Classes, Methods, other JVM objects.
  * size of this area is limited, and much smaller than the heap. So you may run out of PermGen space. 
* jdk8, interned strings stored on heap (young & old generations), along with the other objects created by the application. 
