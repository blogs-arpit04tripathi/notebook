---
layout: post
title: Shared Objects in Microservices
permalink: /:collection/microservices/shared-objects
---

Suppose we have class A defined in microservice A and microservice B is calling an endpoint to get this as response, should we have replica of class definition in microservice B or use a shared library among them?
- Preferred is to use replica of class definition in microservice B.
- If we use shared library, microservices become coupled hence purpose of independent service is defeated, ie. changing the definition requires both microservices to recompile and restart.
- Also shared library will have class definition from all the microservices, suppose we have an ecosystem of 100 microservices and microservice A talks to only 4-5 of them. Why should it have all the 100 microservices class definition?
- **We use SDK**