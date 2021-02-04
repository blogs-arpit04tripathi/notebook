---
layout: post
title: Ordering Aspects
permalink: /:collection/spring/aop/ordering-aspects
---

- If multiple Aspect apply on same pointcut, order is undefined by default.
  - refactor aspects in multiple Aspect classes and use `@Order` annotation.
- Order can also be a negative integer.
- Aspects with same order have undefined order among them.

