---
layout: post
title: Exception Handling
permalink: /:collection/java/exceptions/exception-handling
---


* For runtime error, exception object is created and **JRE** tries to find exception handler for the exception. *(here, in general runtime error is referred, not runtime exception)*
    - **handler found**, exception object **passed to the handler**, known as **catching the exception**. 
    - **no handler found**, then **application throws the exception to JRE and terminates the program**.
* Exception handling can be used to **handle runtime errors only not compile time errors**.

![exception-handling]({{site.cdn}}/java/java-exceptions/exception-handling.png)

* Any uncaught exception will eventually be processed by default handler displaying description and stack trace.
* stack trace shows the sequence of method invocations that led up to the error.

# Chained Exceptions
* Associate one exception with another, 2nd exception describes the cause of the first exception.
* example, ArithmeticException (divide by zero), but actually caused by I/O.
* handles such situations in which layers of exceptions exist.
* `initCause()` - associates causeExc after exception has been created, can be set only once.
  * ***initCause( ) can be called only once for each exception object. If cause set by a constructor, you can’t call.***
* initCause( ) is used for legacy exception classes that don’t support two additional constructors described earlier.
