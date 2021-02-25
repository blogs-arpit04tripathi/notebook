---
layout: post
title: Effectively final and variable capture in Java 8
permalink: /:collection/java/java8/effectively-final
---

* When a lambda expression uses an assigned local variable from its enclosing space there is an important restriction. 
* A lambda expression may only use local variable whose value doesn’t change; restriction is called as ***"variable capture"***.
* local variables that a lambda expression may use are known as "effectively final". 
* An effectively final variable is one whose value does not change after it is first assigned.

Any local variable, formal parameter, or exception parameter used but not declared in a lambda expression must either be declared final or be effectively final, or a compile-time error occurs where the use is attempted.
* Local variables in Java have until now been immune to race conditions and visibility problems because they are accessible only to the thread executing the method in which they are declared. 
* With lambda can be passed to any thread, hence other thread would be able to mutate local variables.
* Even the ability to read the value of mutable local variables from a different thread would introduce the necessity for synchronization or the use of volatile in order to avoid reading stale data.
* Within Lambda expressions you can use effectively final variables from the surrounding scope. Effectively means that it is not mandatory to declare variable final but make sure you do not change its state within the lambda expresssion.

```java
int sum = 0;
list.forEach(e -> { sum += e.size(); });    // illegal; local variable 'sum' is not effectively final
```
The restriction of capture to effectively immutable variables is intended to direct developers’ attention to more easily parallelizable, naturally thread-safe techniques.
```java
int sum = list.map(e -> e.size()).reduce(0, (a, b) -> a+b);
```
The restriction on local variables helps to direct developers using lambdas aways from idioms involving mutation; it does not prevent them. Mutable fields are always a potential source of concurrency problems if sharing is not properly managed.
