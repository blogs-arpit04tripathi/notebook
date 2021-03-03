---
layout: post
title: Config as a Microservice
permalink: /:collection/microservices/configuration/service
---

- Technology Options 
  - Apache Zookeeper
  - ETCD - Distributed Key-Vaule Store
  - Hashicorp Consul
  - Spring Cloud Configuration Service

![]({{site.cdn}}/webservices/microservices/spring-cloud-config-server.png)

**Spring Cloud Configuration Service**
- Add `Config Server` Dependency
- `@EnableConfigServer`
- application.properties -> `spring.cloud.config.server.git.uri=<url of file in git repo>`
- get localhost:8080/\<filname-without-ext>/\<profile>
  - get 'localhost:8080/application/default'

**Spring Cloud Configuration Client**
- Add `Config Client` Dependency
- `spring-cloud-starter-config` in pom.xml
- Additional dependency management section in pom.xml
- application.properties -> `spring.cloud.config.uri=http://localhost:8080/` 

**Microservice Specific Properties**
- Create microservice-name.yml file
- spring.application.name

**Refresh Properties in Real Time**
- `@RefreshScope` on spring components using properties
- POST /actuator/refresh
