---
layout: post
title: Setting Up Docker
permalink: /:collection/containerization/docker/setup
---

# Installing Docker Manually

You can use this simple command to install Docker CE:
```
$ sudo dnf install docker-ce
```

Make sure the Docker daemon has been started and is running:
```
$ sudo systemctl start docker
```

# Docker Hello World

Now that you have the Docker daemon running, you can run your first container by typing:
```
$ sudo docker run hello-world
Unable to find image \'hello-world:latest\' locally
latest: Pulling from library/hello-world
9db2ca6ccae0: Already exists
Digest:
sha256:4b8ff392a12ed9ea17784bd3c9a8b1fa3299cac44aca35a85c90c5e3c7afacdc  
Hello from Docker!
. . .
```

Note that since the image hello-world doesn’t exist yet on the Docker daemon that’s running on your machine, it will pull the image from Docker Hub. This process is similar to what happens with Maven, which will download the Maven dependencies from Maven Central and store them on your local repository. After downloading the image, a container will be created and executed.
