---
layout: post
title: Netflix Ribbon - Client Side Load Balancer
permalink: /:collection/microservices/load-balancing/netflix-ribbon
---

- Ribbon is a client-side load balancer that gives you a lot of control over the behavior of HTTP and TCP clients.
- Feign already uses Ribbon `@FeignClient`.
- group ID `org.springframework.cloud`, artifact ID `spring-cloud-starter-netflix-ribbon`.
- A central concept in Ribbon is that of the named client.
- Netflix Ribbon, it provide several algorithm for Client-Side Load Balancing.
- Spring provide smart RestTemplate for service discovery and load balancing by using `@LoadBalanced` annotation with **RestTemplate** instance.

**References**
- [Spring Cloud- Netflix Eureka + Ribbon Simple Example](https://www.javainuse.com/spring/spring_ribbon)
- [Client Side Load Balancer: Ribbon](https://cloud.spring.io/spring-cloud-netflix/multi/multi_spring-cloud-ribbon.html)

