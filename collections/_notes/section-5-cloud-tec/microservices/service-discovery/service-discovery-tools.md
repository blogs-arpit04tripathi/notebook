---
layout: post
title: Service Discovery Tools
permalink: /:collection/microservices/service-discovery/tools
---

- When service A starts up. It registers itself to some service discovery tool (discovery server) telling I am Service A running on this ip address using this port.
- We can add versions, username-password.
- Most of these service discovery tools are using key value pairs.

**Some Service Discovery Tools**
- Eureka, by Netflix
- Zookeeper, by Apache
- Consul, by HashiCorp
- etcd, by CoreOs
- SkyDNS(built on top of etcd)
- Smartstack, by AirBnB

***Spring Cloud uses client side service discovery.***

Technology used for service discovery by Spring Cloud is Eureka.