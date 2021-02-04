---
layout: post
title: Activating profiles
permalink: /:collection/spring/activating-profiles
---

- Spring provides two separate properties when determining which profiles are active: 
  - `spring.profiles.active`
  - `spring.profiles.default`
- If neither is set, then only those beans that aren’t defined as being in a profile are created. 
- There are several ways to set these properties :
  - As initialization parameters on DispatcherServlet
  - As context parameters of a web application
  - As JNDI entries
  - As environment variables
  - As JVM system properties
  - Using the `@ActiveProfiles` annotation on an integration test class
- You can activate multiple profiles at the same time by listing the profile names, separated by commas.
  - It probably doesn’t make much sense to enable both dev and prod profiles at the same time, but you could enable multiple orthogonal profiles simultaneously.
