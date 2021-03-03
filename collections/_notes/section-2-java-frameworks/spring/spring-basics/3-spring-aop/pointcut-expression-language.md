---
layout: post
title: AspectJ pointcut expression language
permalink: /:collection/spring/aop/pointcut-expression-language
---

- Pointcuts are used to pinpoint where an aspect’s advice should be applied.
  - In Spring AOP, pointcuts are defined using AspectJ’s pointcut expression language.
- Attempting to use any of AspectJ’s other designators cause IllegalArgumentException.
- execution is the primary designator you’ll use in every pointcut definition you write.
  - You’ll use the other designators to constrain the pointcut’s reach.

|AspectJ Designator|	Description|
|---|---|
|**execution()**|	Matches join points that are method executions|
|args()|	Limits join-point matches to the execution of methods whose arguments are instances of the given types|
|@args()|	Limits join-point matches to the execution of methods whose arguments are annotated with the given annotation types|
|this()|	Limits join-point matches to those where the bean reference of the AOP proxy is of a given type|
|target()|	Limits join-point matches to those where the target object is of a given type|
|@target()|	Limits matching to join points where the class of the executing object has an annotation of the given type|
|within()|	Limits matching to join points within certain types|
|@within()|	Limits matching to join points within types that have the given annotation|
|@annotation |	Limits join-point matches to those where the subject of the join point has the given annotation|
