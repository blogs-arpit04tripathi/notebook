---
layout: post
title: Spring Core Introduction
permalink: /:collection/spring/introduction
---

# Introduction to Spring

- Framework to write Enterprise java applications.
- Open source lightweight framework. 
- Provides support to various frameworks - Hibernate, Struts, Tapestry, EJB, JSF etc.
- makes it possible to use plain-vanilla JavaBeans to achieve things that were previously only possible with EJB.
- Key Points: Simplicity, testability, and loose coupling.

# Advantages of Spring Framework

- Predefined Templates
    - Provides templates for JDBC, Hibernate, JPA etc. and hides the basic steps of these technologies.
    - JdbcTemplate
      - No need to write the code for exception handling, creating connection, creating statement, committing transaction, closing connection etc.
      - You need to write the code of executing query only. 
    - Eliminating boilerplate code with aspects and templates.
- Loose Coupling/ Inversion of control (IOC): 
    - The objects give their dependencies instead of creating or looking for dependent objects.
- Easy to test
  - Easy to test due to loose coupling
- Lightweight
    - lightweight because of its POJO implementation. 
    - Spring Framework doesn't force to inherit any class or implement any interface. That is why it is said non-invasive.
- Declarative support
    - through aspects and common conventions
    - provides support for caching, validation, transactions and formatting.
- Transaction Management
    - Generic abstraction layer for transaction management is provided by the Spring Framework. 
    - Spring’s transaction support can be also used in container less environments.
- JDBC Exception Handling: 
    - The JDBC abstraction layer of the Spring offers an exception hierarchy, which simplifies the error handling strategy.

![]({{site.cdn}}/spring/spring-core/spring-core-example.png)