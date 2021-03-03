---
layout: post
title: Extra Operations on the Container
permalink: /:collection/containerization/docker/extra-operations-on-container
---

Although your container is running detached, you can perform some operations on it like checking the logs of your application with the command docker logs plus the name of the container.

```
$ sudo docker logs demo-app
  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/
 :: Spring Boot ::        (v2.0.4.RELEASE)
...
```

If you want to open a terminal session inside the container, you can use the command docker execfollowed by the name of the container and the name of a process that you want to execute. In this case, we want to execute bash in an interactive terminal. Use the following command:
```
$ sudo docker exec -it demo-app bash
```
```
root@ebc74b33f1e5:/# ls
bin          dev           home   lib64   mnt   root  srv  usr
boot             docker-java-home  lib    libx32  opt   run   sys  var
demo-0.0.1-SNAPSHOT.jar  etc           lib32  media   proc  sbin  tmp
```

Once you are inside the container, you can run any Linux command like ls or ps. Note that if you run ls, you should see the file demo-0.0.1-SNAPSHOT.jar that was added during the creation of the image. You can exit from the container terminal and return to your local terminal by typing exit.
