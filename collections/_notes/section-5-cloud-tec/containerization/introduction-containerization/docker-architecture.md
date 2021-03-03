---
layout: post
title: Docker’s Architecture
permalink: /:collection/containerization/docker/architecture
---

Docker uses a typical client-server architecture. The Docker client talks to the Docker daemon, which does the heavy lifting of building, running, and distributing Docker containers. The Docker client and daemon communicate via sockets or through a RESTful API.

![]({{site.cdn}}/webservices/docker/docker-architecture-2.png)

![]({{site.cdn}}/webservices/docker/docker-components.png)

![]({{site.cdn}}/webservices/docker/docker-architecture.png)
