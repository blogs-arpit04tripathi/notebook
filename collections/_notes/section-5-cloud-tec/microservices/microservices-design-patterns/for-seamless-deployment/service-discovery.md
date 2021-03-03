---
layout: post
title: Service Discovery
permalink: /:collection/microservices/patterns/service-discovery
---

- The use of containers leads to dynamic allocation of the IP address.
- This means the address can change at any moment causing a service to break.
- In addition to this, the users have to bear the load of remembering every URL for the services, which become tightly coupled.
- To solve this problem and give users the location of the request, a registry needs to be used.
- While initiation, a service instance can register in the registry and de-register while closing.
- This enables the user to find out the exact location which can be queried.
- In addition, a health check by the registry will ensure the availability of only working instances.
- This also improves the system performance.