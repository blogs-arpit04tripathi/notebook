---
layout: post
title: Service Discovery Types
permalink: /microservices/service-discovery/types
---


```java
@LoadBalanced
private RestTemplate restTemplate;
```

- Client Microservice sends **heart beats** to Discovery Server (Service Registry) to keep the entry alive.

![](https://github.com/arpit04tripathi/files-cdn/raw/cdn/webservices/microservices/service-discovery-eureka.png)

![](https://github.com/arpit04tripathi/files-cdn/raw/cdn/webservices/microservices/service-discovery-types.png)