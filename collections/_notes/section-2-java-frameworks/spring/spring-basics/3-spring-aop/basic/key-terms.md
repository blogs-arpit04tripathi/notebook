---
layout: post
title: Key Terminologies
permalink: /:collection/spring/aop/key-terms
---

- **Aspects**
  - Merger of advice and pointcuts.
  - `what + when` + `where`
  - Aspects have a purpose - a job they’re meant to do.
- **Advice** - defines ***what and when*** of an aspect.
- **Join Points**
  - All the ***points*** within the execution flow of the application ***that are candidates to have advice applied.***
  - This point could be
    - a method being called
    - an exception being thrown
    - a field being modified.
- **Pointcuts**
  - define the ***where*** of an aspect.
  - ***Pointcuts define which join points get advised.***
- **Introductions** - allows you to add new methods or attributes to existing classes.
- **Weaving**
  - process of applying aspects to a target object to create a new proxied object.
  - The aspects are woven into the target object at the specified join points.
