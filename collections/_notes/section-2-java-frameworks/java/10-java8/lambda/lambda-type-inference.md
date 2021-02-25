---
layout: post
title: Type Inference
permalink: /:collection/java/java8/lambda-type-inference
---

- Determining the Type by compiler at compile-time.
- Available before Java 7 too.

```java
String str[] = { "Java 7", "Java 8", "Java 9" };                  // Before Java 7
Map<String,List<Customer>> customerInfoByCity = new HashMap<>();  // Java 7, Right Side Diamond Operator
ToIntBiFunction<Integer,Integer> add = (a,b) -> a + b;            // determines type of parameters in lambda
```
Here Java Compiler observes the type definition available at left-side and determines the type of Lambda Expression parameters a and b as Integers.

# Why lambda expression is called a poly expression?
* type of a lambda expression is inferred from the target. 
* same lambda expression could have different types in different contexts.
* Example - concat and sum.
