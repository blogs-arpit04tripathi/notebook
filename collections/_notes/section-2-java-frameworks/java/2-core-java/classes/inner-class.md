---
layout: post
title: Inner Class (Nested Class)
permalink: /:collection/java/inner-class
---

* define class within a class, ***nested classes***. 
* It is a member of its enclosing class.
  * scope is bounded by the scope of its enclosing class. 
* B defined within A, then B ***does not exist independently*** of A.
* **nested class can access even private members of the container class but not vice-versa**. 
* They are **particularly helpful when handling events**.

# Static nested class
* cannot refer to non-static members of its enclosing class directly, so they are seldom used.

# Inner class
* inner class is a **non-static nested class**.
* has access to all of the variables and methods of its outer class, including private also.
* instance of **Inner** created only in context of **Outer** class otherwise compile-time error.
* can define a nested class within a method block or even in the body of a **for loop**.