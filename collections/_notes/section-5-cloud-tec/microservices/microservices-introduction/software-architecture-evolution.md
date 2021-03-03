---
layout: post
title: Software Architecture Evolution
permalink: /:collection/microservices/software-architecture-evolution
---

![evolution-software-architecture]({{site.cdn}}/webservices/microservices/evolution-software-architecture.png)


**How SOA, monolithic, and Microservices Architectures are different from each other?**
-	**SOA (Service-Oriented Architecture)**: This is a wide collection of services that could communicate together.
-	**Monolithic**: This is highly similar to the big container where all software components of an application are assembled and packed together.
-	**Microservices**: Microservices can be defined as the architectural style that structures an application as a collection of small autonomous services that are modeled around a business domain.

In SOA, 
- we build services for reusability but we don't have clarity of probable usages or applications while in microservices it is part of application and we are aware of the use cases for microservice.
- SOA have very strict contract as clients are not known and changes should not break the old consumer code.
