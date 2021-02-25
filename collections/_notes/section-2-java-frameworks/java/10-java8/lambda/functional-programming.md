---
layout: post
title: Functional Programming
permalink: /:collection/java/java8/functional-programming
---

- Code in OOP
  - Everything is an object, except primitives everything in java existed as objects.
  - All code-blocks/methods/functionas are associated with classes and object, they did not exist independently by itself.
- There was no way of passing a method as argument or returning a method body for that instance.
- With Java 8 functional programming, we can make use of anonymous functions. 

# Why Functional Programming?  
- Doesn't provide any extra capabiltiy as compared to Object Oriented Programming.
- Enables you to write more readable and maintanable code.
- To be used when you need one piece of functionality but not the object.

```java
public void greet(Greeting greeting){
    // Here, Greeting is an interface and implementation decides the behavior
    greeting.perform();
}
```
Here we are not paasing the behavior but a thing (Greeting Implementation) that has the behavior.
- Lambda allows you to pass the action.

```java
public void greet(action){
    action();
}
```
