---
layout: post
title: Strangler Vine Pattern
permalink: /:collection/microservices/patterns/strangler-vine
---

- Struggle of converting a monolithic system to design microservice architecture.
  - Without hampering the working, converting can be extremely tough.
- To solve this problem we have the strangler pattern, based on the vine analogy.
- Strangler pattern is extremely helpful in case of a web application where breaking down a service into different domains is possible.
- Since the calls go back and forth, different services live on different domains. So, these two domains exist on the same URI.
- Once the service has been reformed, it **‘strangles’** the existing version of the application.
- This process is followed until the monolith doesn’t exist.