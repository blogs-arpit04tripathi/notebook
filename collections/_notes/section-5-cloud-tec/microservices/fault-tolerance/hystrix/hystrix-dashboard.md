---
layout: post
title: Microservices
permalink: /:collection/microservices/hystrix/dashboard
---

- Add dependency `spring-cloud-starter-netflix-hystrix-dashboard`
- `@EnableHystrixDashboard` to application class
- `management.endpoints.we.exposure.include=hystrix.stream` to application.properties
- `localhost:8080/hystrix`
