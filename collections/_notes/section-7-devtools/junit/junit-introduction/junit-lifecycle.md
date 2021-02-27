---
layout: post
title: JUnit Lifecycle
permalink: /:collection/junit/lifecycle
---

JUnit 5 creates new instance of test class for every method run.

- @BeforeAll needs to be executed before creating an instance of the test class hence it has to static only.
```java
@BeforeAll
static void beforeAllInit(){
    System.out.println("Before All executed.");
}
```
- To change this behavior, use `@TestInstance` annotation on the test class.
```java
@TestInstance(TestInstance.Lifecycle.PER_CLASS)
class MathUtilTest{...}
```

![junit-lifecycle]({{site.cdn}}/junit/junit-lifecycle.png)
