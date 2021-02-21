---
layout: post
title: Exceptions in Java
permalink: /:collection/java/exceptions/introduction
---


* **Exception** - erroneous event happened during the execution of a program disrupting normal flow.
    - **causes** - wrong data entered by user, hardware failure, network connection failure etc.

# Exception Hierarchy

> Read articel on [Exception Hierarchy Tutorial](https://www.benchresources.net/exception-hierarchy-in-java/){:target="_blank"}

![exception-hierarchy)]({{site.cdn}}/java/java-exceptions/exception-hierarchy-in-java.png "exception-hierarchy")

* `java.lang.Throwable` - **root class for exception and error**
* `java.lang.Exception`
	* super class for all types of Exception, extends Throwable 
	* **due to programmatic logic (recoverable)**.
    * used to create your own custom exception types.
	* checked exception and unchecked exception
    * CheckedExceptions examples - SQLException, IOException (FileNotFoundException).
    * UncheckedExceptions examples - RuntimeException (ArithmeticException, NullPointerException).
* `java.lang.Error`
	- super class for all types of Error.
	- **due to lack of system resources at run-time, non-recoverable**.
	- **errors are unchecked exception, not expected to be caught by your program**.
	- ex. VirtualMachineError (StackOverflowError, OutOfMemoryError), AssertionError, ExceptionInInitializerError.
* RuntimeException
    - subclass of Exception.
    - automatically defined for programs.
    - ex. division by zero, invalid array indexing.
