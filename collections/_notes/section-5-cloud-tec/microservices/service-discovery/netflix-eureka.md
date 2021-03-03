---
layout: post
title: Netflix Eureka
permalink: /:collection/microservices/service-discovery/netflix-eureka
---

- When we start a project, we usally have all the configurations in the properties file.
  - As more and more services are developed and deployed, adding and modifying these properties become more complex.
  - Some services might go down, while some the location might change.
  - This manual changing of properties may create issues.
- Eureka Service Registration and Discovery helps in such scenarios.
  - As all services are registered to the Eureka server and lookup done by calling the Eureka Server.
    - any change in service locations is taken care of automatically.
- Eureka is also known as the ***Netflix Service Discovery Server***.

# Overview of Netflix components
- **Spring Cloud** provides Netflix OSS integrations for Spring Boot apps through autoconfiguration and binding.
- With **annotations** you can configure the common patterns inside your application and build large distributed systems with battle-tested Netflix components.

|Netflix Component Name|	Functionality|
|---      |---|	
|Eureka   |	Service Registration and Discovery|
|Hystrix  |	Circuit Breaker|
|Zuul     |	Server Side Load Balancing<br>Edge Server, Intelligent Routing |
|Ribbon   |	Dynamic Routing and Load Balancer (Client Side Load Balancing)|

> [Microservice Registration and Discovery with Spring cloud using Netflix Eureka](https://www.javainuse.com/spring/spring_eurekaregister){:target="_blank"}

**How Can You Set Up Service Discovery?**  
1. **Client Configuration**
   - can be done easily by using the property files.
   - In the classpath, Eureka searches for eureka-client.properties.
   - It also searches for overrides caused by the environment in property files which are environment specific.
2. **Server Configuration**
  - you have to configure the client first.
  - Once that is done, the server fires up a client which is used to find other servers.
  - The Eureka server, by default, uses the Client configuration to find the peer server.
