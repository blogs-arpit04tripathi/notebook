---
layout: post
title: Configuration Strategies
permalink: /:collection/microservices/configuration/strategies
---

|Specificity|Type|Where|
|---|---|---|
|Microservice Specific|Changing - No|Property File|
|Microservice Specific|Changing - Yes|Config Server|
|Microservice Specific|Environment Config|System Variable with Alias|
|Microservice Specific|Changing - Yes|Config Server|

```properties
<!-- system properties -->
host.env.port=8080          // provider A
host.environment.port=8080  // provider B

<!-- microservice properties -->
env.port=${host.env.port}   // single place to change (alias)
server.port=${env.port}
```
