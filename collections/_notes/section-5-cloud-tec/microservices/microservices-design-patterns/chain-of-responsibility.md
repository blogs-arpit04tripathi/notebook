---
layout: post
title: Chain of responsibility Pattern
permalink: /:collection/microservices/patterns/chain-of-responsibility
---

* produces a single output which is combination of mltiple chanied outputs.
* Use synchronous http request or response for messaging.
* Disadvantage - No output till all services in chain gives response, also cascading failures hence client waits for long without any response.
