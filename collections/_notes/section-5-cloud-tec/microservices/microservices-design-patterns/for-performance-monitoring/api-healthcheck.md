---
layout: post
title: API Health Check
permalink: /:collection/microservices/patterns/api-healthcheck
---

- APIs serve as the building blocks of an online connectivity.
- It is imperative to keep a health check on your APIs on regular basis to realize any roadblock.
- It is often observed that a microservice is up and running yet incapacitated for handling requests. This can be due to many factors:
  - Server Loads
  - User Adoption
  - Latency
  - Error Logging
  - Market Share
  - Downloads
- A service registry periodically appeals to the health check API endpoint to perform a health scan.
  - `HTTP /health`
- health check would provide information
  1. A logic that is specific to your application.
  2. Status of the host.
  3. Status of the connections to other infrastructure or connection to any service instance.