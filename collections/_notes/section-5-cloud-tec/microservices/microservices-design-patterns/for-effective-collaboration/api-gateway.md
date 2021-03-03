---
layout: post
title: API Gateway
permalink: /:collection/microservices/patterns/api-gateway
---

- Backend for Front-End/ API Gateway
- Fetching user-owned resources from multiple microservices using a single UI can be very tricky.
- API gateway acts as a single entry point for all interactions that takes place within the architecture.
  - can act as a proxy server to route requests to microservices 
  - aggregate results from multiple services and send the output to the user.
  - It can handle multiple protocol requests and convert whenever required. (eg. HTTPS to AMQP and vice versa)
- API gateway also helps to establish security by client authorization and exposing relevant APIs with respect to the client.