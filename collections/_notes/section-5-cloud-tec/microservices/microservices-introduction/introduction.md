---
layout: post
title: Microservices
permalink: /:collection/microservices/introduction
---

- Microservices is an architectural style
  - application is structured as a collection of small autonomous services.
    - services are modeled around a business domain.
  - Services are connected but independent in its own way.
    - Can be scaled independently .
    - Failure Isolation.

**When Monolith is broken down to modular microservices, you are exchanging one set of problems with other set of problems.**
- Problems Solved
  - big chunk of code
  - scalability
  - modularity of deployments
- New Problem Set
  - Due to modularity, make sure release process is fine.
  - With Scalability, make sure you have multiple copies and still make your application work.

- Here, Problems to be solved for Monolith Architecture are very specific to your application.
- While for Microservices problem sets are more generic, example load balancing etc.
  - For common problems we have common solution
    - *patterns* - Make microservices work well together like service discovery.
    - *technologies* - Libraries and framworks to solve common problems like eureka, spring cloud.

**Note**: RestTemplate is depricated, now you need to use WebClient which needs reactive programming for providing asynchronous capabilities.

![microservices.png]({{site.cdn}}/webservices/microservices/microservices.png)
