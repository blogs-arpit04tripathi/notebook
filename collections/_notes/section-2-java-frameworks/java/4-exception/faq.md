---
layout: post
title: Exceptions - FAQ
permalink: /:collection/java/exceptions/faq
---

- TOC
{:toc}

<hr><br>

# What is difference between final, finally and finalize in Java?
* final : keyword 
* finally : related to exception handling
* finalize() : method is executed by Garbage Collector before object is destroyed.

# What is OutOfMemoryError in Java? How did you solved that?
* subclass of java.lang.VirtualMachineError thrown by JVM when it ran out of heap memory.
* when not enough space on heap to allocate that object.
* due to system's limitation (memory) rather than programming.
* Might also be caused by a **memory leak**.

Types of OutOfMemoryError in Java
* The java.lang.OutOfMemoryError: Java heap space
* The java.lang.OutOfMemoryError: PermGen space

```java
$>java MyProgram -Xms1024m -Xmx1024m -XX:PermSize=64M -XX:MaxPermSize=256m
```
This is also a chance to impress interviewer by showing your advanced technical knowledge related to finding memory leaks, profiling and debugging.

# What are different scenarios causing “Exception in thread main”?
* UnsupportedClassVersionError: jdk difference
* NoClassDefFoundError
* NoSuchMethodError: run class without main
* ArithmeticException

# Why do you think Checked Exception exists in Java, since we can also convey error using RuntimeException?
* design decision influenced by experience in programming language prior to Java.
* **checked exceptions** – superclass is **Exception**.
* **unchecked exceptions** – superclass are **RuntimeException** and **Error**.
* Checked exceptions - error scenarios not caused by program, ex. FileNotFoundException
* Unchecked exceptions - caused by poor programming, ex. NullPointerException.
* **checked exceptions in java.io package**, must handle when requested resource not available hence checked Exception. 
* To ensure that system resources are released as soon as you are done with that using catch or finally block.
