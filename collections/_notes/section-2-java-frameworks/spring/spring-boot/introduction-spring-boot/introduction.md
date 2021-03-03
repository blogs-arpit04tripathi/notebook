---
layout: post
title: SpringBoot Introduction
permalink: /:collection/spring/boot/introduction
---

![spring-boot-equation]({{site.cdn}}/spring/spring-boot/spring-boot-equation.png)

- **SpringBoot**
  - Spring framework module
  - provides RAD (Rapid Application Development) with starter templates.
  - used to create spring standalone application.
- **Spring**
  - Application Framework to write enterprise java application
  - Programming and Configuration Model
    - You focus on building bussiness services and spring take care of common concerns.
    - like handling http requests, running queries etc.
  - Infrastructure Support : like support for rdbms, mongo etc.
- **Problems with Spring**
  - Huge Framework
  - Multiple Setup and Configuration Steps
  - Multiple Build and Deploy Steps

# Benefits of SpringBoot
- Framework on top of Spring, eases bootstrapping and development of new spring applications.
- **Opiniated default Configurations** to avoid lot of boilerplate code, we can focus on business logic rather than configurations.
    - Opinionated ‘starter’ dependencies to simplify build and application configuration
    - Automatic config for Spring functionality based on the artifacts it finds on the classpath – whenever possible
    - Resolve needed dependency
- Creates container for running the code
- Starts embedded tomcat instance
    - Embedded server to avoid complexity in application deployment
- Provides non-functional features like Metrics, Helth check, and externalized configuration
- includes auto-configuration for following template engines
  - FreeMarker
  - Thymeleaf
  - Mustache

![spring-projects]({{site.cdn}}/spring/spring-boot/spring-projects.png)
