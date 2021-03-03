---
layout: post
title: Publishing Your Image on Docker Hub
permalink: /:collection/containerization/docker/publih-to-docker-hub
---

To publish your image on Docker Hub, you need to sign up for a free account.  
Now that you have a Docker Hub account, you can log in by running docker login:
```
$ sudo docker login
Login with your Docker ID to push and pull images from Docker Hub. If you don't have a Docker ID, head over to https://hub.docker.com to create one.
Username:
Password:
Login Succeeded
```
Note that the images published on Docker Hub need to have your username as a prefix. When we created our demo image, we didn’t add the username prefix, but we can do it now using the command docker tag.
```
$ docker tag demo <your username>/refcard-demo
```
Now, the same image has two tags (demo and rafabene/refcard-demo). You can use any tag that you want. The only requirement to push to Docker Hub is to have your username as a prefix.

To push the new tag to Docker Hub, just execute the command docker push \<your username\>/image-name. Example:
```
$ sudo docker push <your username>/refcard-demo
The push refers to repository [docker.io/<your username>/refcard-demo]
4c7628270fc7: Pushed
. . .
25edbec0eaea: Mounted from library/openjdk
latest: digest: sha256:92cddb652d55db14c3f697d25f4c93a145f9b287522ae43afe623fe130437d35 size: 2212
```
Now, your image /refcard-demo is available to be used by any Docker daemon worldwide.
