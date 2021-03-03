---
layout: post
title: Microservices around similar Business Capability
permalink: /:collection/microservices/patterns/around-similar-capability
---

- Despite segregating on the basis of business capabilities, microservices often come up with a greater challenge.
- What about the common classes among the services? Well, decomposing these classes known as ‘God Classes’ needs intervention.
  - For example, in case of an e-commerce system, the order will be common to several services such as order number, order management, order return, order delivery etc. 
- To solve this issue, we turn to a common microservice design principle known as Domain-Driven Design (DDD).
- In Domain-Driven Design, we use subdomains.
- These subdomain models have defined scope of functionality which is known as bounded context.
- This bounded context is the parameter used to create each microservice thus overcoming the issues of common classes.

