---
layout: post
title: Issues with Microservices
permalink: /:collection/microservices/issue-with-microservices
---

- A Microservice goes down?
  - run multiple instances.
- A Microservice instance is slow.
  - An unrelated service call also becomes slow, this is caused by servlet thread pool being exhausted.
  - **Solution 1** - apply timeout.
    - This solves the solution partly, breaks if requests per seconds exceeds timeout capacity.
  - **Solution 2** - Use `Circuit Breaker Pattern`
    - Detect something is wrong.
    - Take temporary steps to avoid the situation from getting worse.
    - Deacivate the "problem component" so that it doesn't affect the downstream components.
    - circuit breaker can be reset (manually or programatically) to resume normal operation.
  - **Solution 3** - `BulkHead Pattern`

# Servlet thread pool Exhaused (in spring boot)

***Immediate Failures***
- can be handled by try catch
- User will continuously keep sending the request without any knowledge of service being down.
- already 10 times failed, why call for 11th time

***Timeout Failures***
- All threads of the pool are exhausted ie. service overloaded. (Service resource exhausted)
- User keeps waiting for longer time, hence bad user experience.
- can cause cascading failures in other microservices.
    * A --> B and uses up all servlet threads then, C --> B will also fail.
- **Solution** : Circuit Breaker Pattern
    * Stop calling the overloaded service and allow it to recover.
    * Add request interceptor to immediately return default response for recovery period.
    * interceptor status flag changed once service is up again.
    * failure threshold is monitored to change status in interceptor service.
    * Status - `OPEN`, `CLOSED`, `HALF-OPEN`
    * track % of calls failing is the best approach for last N calls.
    * after expected recovery time for service is over, service can be made HALF_OPEN(partially allow).
    * Implementation - Hystrix, resilience4j
        - Implemented using decorator pattern

![]({{site.cdn}}/webservices/microservices/circuit-breaker-check.png)
