---
layout: post
title: Create Container Image for Spring Boot Application
permalink: /:collection/containerization/docker/create-container-image
---

The easiest way to create a Docker image is to write a Dockerfile. It contains a series of commands that customize an image based on a previous one. For our application, we will start from the existing OpenJDK 10 image, add our JAR file, and define the default command that will execute when the container starts.

The Dockerfile below is also available to be copied here. This file should be in the same folder of the project.
```
# Our base image that contains OpenJDK
FROM openjdk 
# Add the fatjar in the image
COPY target/demo-0.0.1-SNAPSHOT.jar / 
# Default command
CMD java -jar /demo-0.0.1-SNAPSHOT.jar
```
Before adding the JAR file to the image, we needed to create it using the command mvn package. Now that we have a Dockerfile, we can execute the build of the JAR and the Docker image using the following commands:
```
$ mvn package
. . .
$ sudo docker build -t demo .
Sending build context to Docker daemon  17.87MB
Step 1/3 : FROM openjdk
Step 2/3 : COPY target/demo-0.0.1-SNAPSHOT.jar /
Step 3/3 : CMD java -jar /demo-0.0.1-SNAPSHOT.jar
. . .
Successfully built 4df92f5aa7f6
Successfully tagged demo:latest
```
The flag -t on the docker build command specifies the name/tag of the image. Using a tag called demoallows you to refer to this image by its name when you need to create a container instance. The last parameter for docker build is the path of Dockerfile. Since the Dockerfile is in the same folder of your project, the . will instruct the Docker daemon to use the file in the same folder that you execute the command.
