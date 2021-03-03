---
layout: post
title: Running the Application Inside the Container
permalink: /:collection/containerization/docker/run-application-in-container
---

The previously created image called demo is available locally. You can check the existing images available locally through the command docker images.

The demo image can now be used to create a new container instance with the following command:
```
$ sudo docker run -d --name demo-app -p 8080:8080 demo
582b891f7ffa307ad08f6669cfb473ac822dc49d29b80dc18477d4a120d2a023
```
The flag -d instructs the Docker daemon to detach from the container after the execution of the command. The flag --name gives the name demo-app to this container. If you don’t specify a name, Docker will create a random name for you.

By default, you can’t access any ports in the container unless you specify the mapping between the Docker daemon port and the container port. This feature is useful to allow the same application that is running on port 8080 to bind to different ports if you decide to run multiple containers. In our case, we are mapping port 8080 from the Docker daemon to port 8080 of the container through the flag -p 8080:8080.

Finally, we specify the name of the image that we want to use to create the container. In this case, we used the demo image created previously. After the execution of the command, it will show a hash number that identifies your container. You can verify the containers that are running with the following command:
```
$ sudo docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             .         STATUS              PORTS                    NAMES
ebc74b33f1e5        demo                "/bin/sh -c 'java -j…"   5 minutes ago       Up 5 minutes        0.0.0.0:8080->8080/tcp   demo-app
```

Now that your container is being executed, you can open your browser again in the URL http://localhost:8080/api/hello. You will see the same result that you had previously, but this time, your application is running inside the container.
