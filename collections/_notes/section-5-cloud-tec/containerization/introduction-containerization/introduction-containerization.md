---
layout: post
title: Containerization Introduction
permalink: /:collection/containerization/introduction
---

**Linux container**
- A Linux container is an operating system-level virtualization technology that, unlike a virtual machine (VM), shares the host operating system kernel and makes use of the guest operating system libraries for providing required OS capabilities.
- Since there is no dedicated operating system, containers are more lightweight and start much faster than VMs.

**Docker**
- Docker was developed as an open platform for packaging, deploying, and running distributed applications.
- Docker uses its own Linux container library called libcontainer.
- It became the most popular and widely used container management system.
- Later, this library was donated to OCI (Open Container Initiative) with the name of runc.

**Why Do We Need Containers for Microservices?**
- To manage a microservice-based application, containers are the easiest alternative.
- It helps the user to individually deploy and develop.
- You can also use Docker to encapsulate microservices in the image of a container.
- Without any additional dependencies or effort, microservices can use these elements.

**What is the use of Docker?**  
- Docker offers a container environment which can be used to host any application.
- This software application and the dependencies that support it which are tightly-packaged together.

**What is Docker? How to deploy Spring Boot Microservices to Docker?**  
-	[What is Docker](https://www.javainuse.com/devOps/docker){:target="_blank"}
-	[Deploying Spring Based WAR Application to Docker](https://www.javainuse.com/devOps/docker/docker-war){:target="_blank"}
-	[Deploying Spring Based JAR Application to Docker](https://www.javainuse.com/devOps/docker/docker-jar){:target="_blank"}

**What is Docker? How to deploy Spring Boot Microservices to Docker?**  
-	[What is Docker](https://www.javainuse.com/devOps/docker){:target="_blank"}
-	[Deploying Spring Based WAR Application to Docker](https://www.javainuse.com/devOps/docker/docker-war){:target="_blank"}
-	[Deploying Spring Based JAR Application to Docker](https://www.javainuse.com/devOps/docker/docker-jar){:target="_blank"}

**How to deploy multiple microservices to docker?**
- [Deploying Multiple Spring Boot Microservices using Docker Networking](https://www.javainuse.com/devOps/docker/docker-networking){:target="_blank"}
