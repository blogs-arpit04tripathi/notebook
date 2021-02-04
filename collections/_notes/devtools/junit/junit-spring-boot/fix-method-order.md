---
layout: post
title: FixMethodOrder Annotation
permalink: /:collection/junit/fix-method-order
---

**How to test methods in specific order using JUnit4?**
- JUnit currently allows test methods run ordering using class annotations:
  * @FixMethodOrder(MethodSorters.NAME_ASCENDING)
  * @FixMethodOrder(MethodSorters.JVM)
  * @FixMethodOrder(MethodSorters.DEFAULT)
 
 ```java
@FixMethodOrder(MethodSorters.NAME_ASCENDING)
public class SampleTest {
    @Test
    public void testAcreate() {
        System.out.println("first");
    }
    @Test
    public void testBupdate() {
        System.out.println("second");
    }
    @Test
    public void testCdelete() {
        System.out.println("third");
    }
}
 ```
 ```java
 @Test
public void testOrder1() { test1(); test3(); }
```
