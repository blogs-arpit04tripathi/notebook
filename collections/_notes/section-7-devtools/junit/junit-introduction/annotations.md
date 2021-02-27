---
layout: post
title: JUnit 5 Annotations
permalink: /:collection/junit/annotations
---



Annotaions||
---|---
@BeforeEach|The annotated method will be run before each test method in the test class.
@AfterEach|The annotated method will be run after each test method in the test class.
@BeforeAll|The annotated method will be run before all test methods in the test class. This method must be static.
@AfterAll|The annotated method will be run after all test methods in the test class. This method must be static.
@Test|It is used to mark a method as junit test
@DisplayName|Used to provide any custom display name for a test class or test method
@Disable|It is used to disable or ignore a test class or method from test suite.
@Nested|Used to create nested test classes
@Tag|Mark test methods or test classes with tags for test discovering and filtering
@TestFactory|Mark a method is a test factory for dynamic tests

```java
@Test(timeout = time)
@Test(expected = exception.class)
```
```java
@RepeatedTest(3)
void testCircleArea(RepetitionInfo repetitionInfo){
    if(repetitionInfo.getCurrentRepetition == 1){...}
    ...
    // Here JUnit 5 gives RepetitionInfo by Dependency Injection
}
```
```java
public class AppTest {
    @BeforeAll
    static void setup() {
        System.out.println("@BeforeAll executed");
    }

    @BeforeEach
    void setupThis() {
        System.out.println("@BeforeEach executed");
    }

    @Tag("DEV")
    @Test
    void testCalcOne() {
        System.out.println("======TEST ONE EXECUTED=======");
        Assertions.assertEquals(4, Calculator.add(2, 2));
    }

    @Tag("PROD")
    @Disabled
    @Test
    void testCalcTwo() {
        System.out.println("======TEST TWO EXECUTED=======");
        Assertions.assertEquals(6, Calculator.add(2, 4));
    }

    @AfterEach
    void tearThis() {
        System.out.println("@AfterEach executed");
    }

    @AfterAll
    static void tear() {
        System.out.println("@AfterAll executed");
    }
}
```

![]({{site.cdn}}/junit/nested-unit-tests.png)
