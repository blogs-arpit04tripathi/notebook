---
layout: post
title: Spring AOP Introduction
permalink: /:collection/spring/aop/introduction
---

- **Aspect-oriented programming (AOP)** separates cross-cutting concerns from the business logic.
  - DI helps you decouple application objects from each other.
  - AOP helps you decouple cross-cutting concerns from the objects they affect.
- **cross-cutting concern**
  - functionality that affects multiple points of an application.
  - Security - many methods in an application can have security rules applied to them.
  -	Logging, security, and transaction management are such aspects.
-	Application objects should focus on the business domain problems.
- ***Aspect***
  - Core of AOP, encapsulates behaviors that can affect multiple classes into reusable modules.
  - Aspects offer an alternative to inheritance and delegation that can be cleaner in many circumstances.

![]({{site.cdn}}/spring/spring-aop/aop.png)

# Benefits
- Centralized logic for each concern
  - declaratively define how and where this functionality is applied without modifying the class.
-	your service modules are cleaner because they only contain code for core functionality.

# Concern vs Cross-cutting Concerns

![]({{site.cdn}}/spring/spring-aop/cross-cutting-vs-concern.png)

![]({{site.cdn}}/spring/spring-aop/aspects.png)
