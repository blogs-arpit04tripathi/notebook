---
layout: post
title: Erasure
permalink: /:collection/java/generics/erasure
---

- TOC
{:toc}

<hr><br>

* compatibility with preexisting, non-generic code, is achieved through ***erasure***.

# How erasure works?
* On compilation, all generic type information is removed (erased). 
* replaces type parameters with their bound type, **Object** by default, and apply appropriate casts. 
* No type parameters exist at run time. They are simply a source-code mechanism.

# Bridge Methods
* Needed for situation where type erasure in superclass and subclass does not produce same erasure method. 
* A method is generated that uses type erasure of superclass, and calls the method with subclass type erasure. 
* bridge methods only occur at the ***bytecode level, are not seen by you, and are not available for your use***.

```java
class Gen<T> {   // situation creating a bridge method.
  T ob; 
  Gen(T o) { ob = o; }
  T getob() { return ob; }
}
class Gen2 extends Gen<String> {
 Gen2(String o) { super(o); }
 String getob() {  return ob;   }
}

class BridgeDemo {
 public static void main(String args[]) {
  Gen2 strOb2 = new Gen2("Generics Test");
  System.out.println(strOb2.getob());
 }
}
```
* Due to type erasure, the expected form of getob( ) will be
Object getob() { // ...
* compiler generates a bridge method that calls the String version. 
* examine class file Gen2 by javap, you see below methods:

```java
class Gen2 extends Gen<java.lang.String> {
   Gen2(java.lang.String);
   java.lang.String getob();
   java.lang.Object getob();  // bridge method
}
```
Normally, same signature would cause an error, but because this does not occur in your source code, it does not cause a problem and is handled correctly by the JVM.

# Ambiguity Errors

* Due to erasure, two distinct generic declarations resolve to same erased type, causing a conflict.

```java
class MyGenClass<T, V> {
 T ob1;      V ob2;
 // ambiguous, will not compile.
 void set(T o) { ob1 = o; }
 void set(V o) { ob2 = o; }
}
```
* There are two ambiguity problems here:
	- T and V can be of same types. 
        - MyGenClass<String, String> obj = new MyGenClass<>()
        - both versions of set( ) identical, an error.
	- type erasure of set( ) reduces both versions to the following: 
        - void set(Object o) { // ... both set() are inherently ambiguous.

```java
class MyGenClass<T, V extends Number> { // almost OK!
MyGenClass<String, Number> x = new MyGenClass<String, Number>();
MyGenClass<Number, Number> y = new MyGenClass<Number, Number>();
```
* Better to use two separate method names, rather than trying to overload **set()**. 
* Often, ambiguity can be resolved by restructuring the code as it generally means a conceptual error in your design.
