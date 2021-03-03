---
layout: post
title: Individual Database per Service
permalink: /:collection/microservices/patterns/individual-db
---

- Usually applied in Domain Driven Designs.
- One database per service articulates the entire database to a specific microservice.
- Due to the challenges and lack of accessibility, a single database per service needs to be designed.
- This data is accessible only by the microservice.
- This database has limited access for any outside microservices.
- The only way for others to access this data is through microservice API gateways.