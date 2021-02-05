---
layout: post
title: JUnit 5 Assumptions
permalink: /:collection/junit/assumptions
---

* Assumptions class provides static methods to support conditional test execution based on assumptions. 
* A failed assumption results in a test being aborted. 
* Assumptions are typically used whenever it does not make sense to continue execution of a given test method. In test report, these test will be marked as passed.
* JUnit jupiter Assumptions class has two such methods: `assumeFalse()`, `assumeTrue()`.
```java
public class AppTest {
    @Test
    void testOnDev() {
        System.setProperty("ENV", "DEV");
        Assumptions.assumeTrue("DEV".equals(System.getProperty("ENV")), AppTest::message);
    }      
    @Test
    void testOnProd() {
        System.setProperty("ENV", "PROD");
        Assumptions.assumeFalse("DEV".equals(System.getProperty("ENV"))); 
    }
    private static String message () {
        return "TEST Execution Failed :: ";
    }
}
```
