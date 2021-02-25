---
layout: post
title: Lambda Expressions
permalink: /:collection/java/java8/lambda-expression
---

- a function that can be referenced and passed around as an object.
- Anonymous function, not belong to any class ie. Lambda functions can exist in isolation.
- Declarative coding and code maintainability as well.
- Allows users to pass methods as arguments, helps remove a lot of boilerplate code. (create 1 time classes and interfaces)
- These functions can be treated as values ie. assign a block of code to variable rather than the execution output of the block of code.
- Lambda Functions have no access modifiers (private, public or protected), no return type declaration and no name.
- `->` is called **Lambda arrow**.
- lambda expressions are a natural replacement for anonymous classes as method arguments.

# Why Lambdas ?
- enable functional programming
- readable and concise code
- Easier-to-use API and libraries
- Enables support for parallel processing
- No separate class created as opposed to anonymous class, reduced memory footprint in jar thus improved performance.

```java
aBlockOfCode = () - > System.out.println("Hello World!");

doubleNumberFunction = (int a) - > a * 2;

addFunction = (int a, int b) - > a + b;
addFunction = (a, b) - > a + b;
// above is also valid as Functional Interface have only 1 method and argument type can be inferred

safeDivideFunction = (int a, int b) - > {
    if (b == 0) return 0;
    return a / b;
};

(Comma separated Arguments) - > expression body
Runnable runnable = () - > System.out.println("Running thread by Lambda");
```
