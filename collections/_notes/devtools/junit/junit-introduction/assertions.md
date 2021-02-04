---
layout: post
title: JUnit 5 Assertions
permalink: /:collection/junit/assertions
---


* Assertions help in validating the expected output with actual output of a testcase. 
* To keep things simple, all JUnit Jupiter assertions are static methods in the `org.junit.jupiter.Assertions` class e.g. `assertEquals()`, `assertNotEquals()`.

```java
assertEquals(expected, actual)
assertArrayEquals(expectedArray, actualArray)
assertIterableEquals(expectedIterable, actualIterable)
```
```java
void testCase(){
    //Test will pass
    Assertions.assertNotEquals(3, Calculator.add(2, 2));
    //Test will fail
    Assertions.assertNotEquals(4, Calculator.add(2, 2), "Calculator.add(2, 2) test failed"); 
}
```
```java   
//Test will fail - Lazy Assert Messages
Supplier<String> messageSupplier  = ()-> "Calculator.add(2, 2) test failed";
Assertions.assertNotEquals(4, Calculator.add(2, 2), messageSupplier);
```
```java
//Assert Exception Throw
Assertions.assertThrows(ArithmeticException.class, () -> Calculator.divide(2, 0), "Divide by zero should throw.");
```
```java
@Test
void assertAllProperties_fail() {
    Address address = new Address("New City", "Some Street", "No");
    assertAll("address", 
        () - > assertEquals("Neustadt", address.city),
        () - > assertEquals("Irgendeinestraße", address.street),
        () - > assertEquals("Nr", address.number)
    );
}

// Output
org.opentest4j.MultipleFailuresError: address (3 failures)
	expected: <Neustadt> but was: <New City>
	expected: <Irgendeinestraße> but was: <Some Street>
	expected: <Nr> but was: <No>
```
