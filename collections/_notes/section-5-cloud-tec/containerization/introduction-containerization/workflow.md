---
layout: post
title: Docker Basic Workflow
permalink: /:collection/containerization/docker/workflow
---

The typical workflow in Docker involves building an image from a Dockerfile or pulling an image from a registry (like Docker Hub). Once the image is available on the Docker Host, a container can be launched as a runtime environment. Docker Hub has approximately 100 “official” images published by software vendors — eliminating the need to build a Tomcat or MySQL image from scratch in most cases. Once a container is running, it can be stopped, started, or restarted using the CLI. If changes are made to the container, a user can commit the changes made into a new image with either the same tag (or version) or a different one. The new image can, of course, then be pushed to a registry (like Docker Hub).

Instead of listing all the supported workflows, this Refcard walks through a basic Spring Boot Java application — starting from basic container’s use cases to more advanced ones.

![]({{site.cdn}}/webservices/docker/docker-workflow.png)
