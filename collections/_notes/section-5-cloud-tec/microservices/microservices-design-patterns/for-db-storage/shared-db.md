---
layout: post
title: Shared Database per Service
permalink: /:collection/microservices/patterns/shared-db
---

- In Domain Driven Design, a separate database per service is feasible, but in an approach where you decompose a monolithic architecture to microservice, using a single database can be tough.
- So while the process of decomposition goes on, implementing a shared database for a limited number of service is advisable.
- This number should be limited to 2 or 3 services.
- This number should stay low to allow deployment, autonomy, and scalability.
- Drawbacks
  - Duplication of data and consistency.
  - transaction requires query data from multiple services.
  - Denormalization of data is not easy.