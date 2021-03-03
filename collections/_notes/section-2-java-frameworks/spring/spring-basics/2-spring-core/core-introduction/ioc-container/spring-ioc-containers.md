---
layout: post
title: Spring IOC Container
permalink: /:collection/spring/core/ioc-container
---

In a Spring-based application, your application objects live in the Spring container.  
Spring container uses DI to manage components that make up an application. These objects support reuse and are easy to unit test.

**Responsibilities of the Spring Container**
- Creates the objects (Spring Beans)
- Wires them together (associations)
- Configures them, and 
- Manages their complete lifecycle

![]({{site.cdn}}/spring/spring-core/spring-container.png)

- Container gets its instructions on what objects to instantiate, configure, and assemble by reading the configuration metadata provided. 
- Configuration metadata - XML, Java annotations, or Java code. 
- The Spring IoC container makes use of Java POJO classes and configuration metadata to produce a fully configured and executable system or application.

