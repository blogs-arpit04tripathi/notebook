---
layout: post
title: Service Discovery Types
permalink: /:collection/microservices/service-discovery/types
---


```java
@LoadBalanced
private RestTemplate restTemplate;
```

- Client Microservice sends **heart beats** to Discovery Server (Service Registry) to keep the entry alive.

![]({{site.cdn}}/webservices/microservices/service-discovery-eureka.png)

![]({{site.cdn}}/webservices/microservices/service-discovery-types.png)