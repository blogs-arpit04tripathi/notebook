---
layout: post
title: Java8 FAQ
permalink: /:collection/java/java8/faq
---

- TOC
{:toc}

<hr><br>

# MetaSpace Diagram?
![metaspace]({{site.cdn}}/java/java8/metaspace.png)

# What is MetaSpace in Java8? How does it differ from PermGen Space?
* With JDK8, the permGen Space has been removed. 
* So where will the metadata information be stored now?
  - This metadata is now stored in a native memory are called as "**MetaSpace**".
  - This memory is not a contiguous Java Heap memory. It allows for improvements over PermGen space in Garbage collection, auto tuning, concurrent de-allocation of metadata.

# What are the new JVM arguments introduced by Java 8?
* In Java 8, PermGen space of ClassLoader is removed.  It has been replaced with MetaSpace.
* Now we can set the initial and maximum size of MetaSpace.
* The JVM options -XX:PermSize and –XX:MaxPermSize are replaced by -XX:MetaSpaceSize and -XX:MaxMetaspaceSize respectively in Java 8.

# What is Nashorn in Java?
* This is the new Java processing [engine for Java platform](https://www.educba.com/cheat-sheet-java/) which is shipped in Java 8. 
* Until JDK 7 Java platform used Rhino as the processing engine. It was a Javascript processing engine. 
* Nashorn provides better compliance with the ECMA normalized [JavaScript specification](https://www.educba.com/uses-of-javascript/).
* It also provides better runtime performance than its previous versions.

# What is jjs?
In Java 8, jjs is the new executable or command line tool used to execute Javascript code at the console.

# What are the popular annotations introduced in Java 8?
Some of the popular annotations introduced in Java 8 are:
* ***@FunctionalInterface***: This annotation is used to mark an interface as Functional Interface. As mentioned earlier, A FunctionalInterface can be used for lambda expressions.
* ***@Repeatable***: This annotation is used for marking another annotation. It indicates that the marked annotation can be applied multiple times on a type.

# What is StringJoiner?
* StringJoiner - util method to construct different strings separated with desired delimiters. 
* StringJoiner(CharSequence delimiter), StringJoiner(CharSequence delimiter, CharSequence prefix, CharSequence suffix).

```java
StringJoiner strJoiner = new StringJoiner(".");
strJoiner.add("Buggy").add("Bread");
System.out.println(strJoiner);         // prints Buggy.Bread
```