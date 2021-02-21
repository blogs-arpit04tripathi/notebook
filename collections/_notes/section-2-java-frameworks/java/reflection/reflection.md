---
layout: post
title: Java Reflection
permalink: /:collection/java/reflection
---

- TOC
{:toc}

<hr><br>

* **Java Reflection** is a process of examining or modifying the run time behavior of a class at run time.
* java.lang and java.lang.reflect packages provide classes for java reflection. 
* With java reflection we can inspect a class, interface, enum, get their structure, methods and fields information at runtime even though class is not accessible at compile time. 
* We can also use reflection to instantiate an object, invoke it’s methods, change field values.

# Where it is used
**Reflection** in Java is a very powerful concept and it’s of little use in normal programming but it’s the backbone for most of the Java, J2EE frameworks. Some of them are:
* JUnit – uses reflection to parse @Test annotation to get the test methods and then invoke it. 
* Spring – dependency injection, read more at Spring Dependency Injection
* Tomcat web container to forward the request to correct module by parsing web.xml files and request URI.
* Eclipse auto completion of method names 
* Struts
* Hibernate

The list is endless and they all use java reflection because all these frameworks have no knowledge and access of user defined classes, interfaces, their methods etc.

|*Drawbacks*||
---|---
**Poor Performance**	    |resolves the types dynamically, it involves processing like scanning the classpath to find the class to load, causing slow performance.
**Security Restrictions**	|Reflection requires runtime permissions that might not be available for system running under security manager. This can cause you application to fail at runtime because of security manager.
**Security Issues**	        |Using reflection, we can access part of code that we are not supposed to access, for example we can access private fields of a class and change it’s value. This can be a serious security threat and cause your application to behave abnormally.
**High Maintenance**	    |Reflection code is hard to understand and debug, also any issues with the code can’t be found at compile time because the classes might not be available, making it less flexible and hard to maintain.
