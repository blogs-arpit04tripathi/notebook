---
layout: post
title: Overloading vs Overriding
permalink: /:collection/java/overloading-vs-overriding
---

# What is Overloading?
* two methods with same name but different method signature.
* Overloaded in the same class.
* Overloaded methods binded by [static binding](https://javarevisited.blogspot.com/2012/03/what-is-static-and-dynamic-binding-in.html) at compile time. 
* During compilation, method calls binded to actual methods.
* Overloaded methods are **fast due to this compile-time binding as no check or binding required during runtime**.
* **Two overloaded methods must have a different signature.**
* **Method signature** in Java consist of:
	* number of arguments.
	* Type of argument.
	* Order of argument.
	* ***return type is not*** part of method signature.

# What is Overriding?
* You can only override method in sub class, not in the same class.
* method with same name and signature in super and sub class or interface and implementation. 
* **can not override private, static and final method** in Java as they are binded at **compile time (static binding)**.
* **private and static method can be hidden (method hiding)**, same name and signature in sub class.
* Overridden method is **binded at runtime, dynamic binding**.
* override all abstract method unless your class is not abstract if you are extending abstract class or implementing interface.
* **@Override** while overriding a method.
  * **annotation not compulsary, but highly recommended**. 
  * It helps prevent the case when you write a function that you think overrides another one but you misspelled something and you get completely unexpected behavior.

# Method hiding in Java
```java
Parent parent = new Child();
Child child = new Child();
parent.staticMethod();	        // Parent Static Method is called
parent.nonStaticMethod          // Child's Non Static Method is called
child.staticMethod              // Child's Static Method is called
```
