---
layout: post
title: String Literal Pool
permalink: /:collection/java/strings/string-literal-pool
---


* String objects are immutable, cannot be changed once created.
* concat - If the length of the argument string is 0, then this String object is returned. **Otherwise, a new String object is created.**

# Storage of Strings - The String Literal Pool

* ***String Literal Pool*** - collection of references to String objects, while the actual String Objects live on the heap. 
* This is feasible due to String immutable nature.
* String Literal Pool (**constant table**) is application level, not class or package level.

# How it is accomplished
* When .java file is compiled into .class file, String literals are noted in a special way, just as all constants are. 
* When class is [loaded](https://docs.oracle.com/javase/specs/jls/se8/html/jls-12.html#jls-12.2) (prior to initialization), JVM checks if String literal is already referenced from the heap.
* If found, references to that string literal is simple replaced with reference in String Literal Pool.
* If not, creates a String instance on heap and adds a reference to the constant table. 

```java
String one = "string";
String two = " string ";
System.out.println(one.equals(two));
System.out.println(one == two);

String two = new String("string ");
two.intern();
```

* With "new" keyword, references of both are kept in constant table (String Literal Pool), but new object created at run-time.
* *[intern()](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html#intern) method looks for referenced in String Literal Pool and returns the reference, even for new keyword.*
* Strings created at run-time will always be distinct from those created from String Literals.
* reuse String Literals with run-time Strings via intern() method.
* equals() – to check equality.
* **String literals are by default interned**.

![string-literal-new.png]({{site.cdn}}/java/strings/string-literal-new.png)

**What makes an object eligible for garbage collection?**  
When object is no longer referenced from an active part of application.

**what is special about garbage collection for String literals?**
* String literals always have a reference to them from the String Literal Pool, not eligible for garbage collection ever.
* object is always reachable via intern() method.

**how many objects are available for garbage collection?**
```java
public static void main(String[] args) {
   String one = "someString";
   String two = new String("someString");
   one = two = null;
}
```
![how-many-objects]({{site.cdn}}/java/strings/how-many-objects.png)

The answer is ***1***.

**Will it create 5 new strings in memory and lead to a performance hit?**
```java
String longString = "abc" + "def" + "ghi" + "jkl" + "mnop";    // evaluated at compile time, only 1 string created 
String longString = "This string is very long.";
String other = "This string" + " is " + "very long.";    // == is true
String is = " is ";
String other = "This string" + is + "very long.";        // == false
```