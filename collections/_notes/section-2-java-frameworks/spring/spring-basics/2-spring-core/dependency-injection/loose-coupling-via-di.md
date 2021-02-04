---
layout: post
title: Loose coupling through DI and interface orientation
permalink: /:collection/spring/loose-coupling-via-di
---

**What do you mean by Dependency Injection?**  
-	Dependency Injection (DI) is a design pattern that removes the dependency from the programming code so that it can be easy to manage and test the application. 
- Dependency Injection makes our programming code loosely coupled
  - objects are given their dependencies at creation time by some third party that coordinates each object in the system.
  - Objects aren’t expected to create or obtain their dependencies.
- `@Autowired` is used, IoC container will wire them up together.

**Dependency Lookup**
- approach where we get the resource after demand. 
- There can be various ways to get the resource for example:
  -	`A obj = new AImpl();`
  -	`A obj = A.getA();`
- Here are mainly two problems of dependency lookup :
  - **Tight coupling** – makes the code tightly coupled, resource change needs a lot of code modification
  - **Not easy for testing** – troublesome black box testing.
