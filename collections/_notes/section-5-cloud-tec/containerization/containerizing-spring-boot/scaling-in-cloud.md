---
layout: post
title: Scaling Your Application in the Cloud
permalink: /:collection/containerization/docker/scaling-in-cloud
---

Every time you execute the docker run command, it creates a single container running in a single machine. Now, imagine that you need to execute a fleet of containers on multiple servers. You will face the following challenges:
-	How to scale?
-	How to avoid port conflicts?
-	How to manage them in multiple hosts?
-	What happens if a host has a trouble?
-	How to keep them running?
-	How to update them?
-	Where are my containers?

The answer to address all these challenges is using a container orchestration solution like Kubernetes. The easiest way to try Kubernetes and also have other features like image build automation, deploy automation, self-service catalog, and CI/CD pipelines is through the usage of OpenShift.

Red Hat® OpenShift® is the industry’s most secure and comprehensive enterprise-grade container platform based on industry standards, Docker, and Kubernetes. It is designed to provide ease of use, making Dev and Ops lives easier. Let’s deploy our application on OpenShift so you can understand some of its functionalities.

Go to https://www.openshift.com/ and create a free trial account. This account allows you to experiment OpenShift online with a limit of 1GB of RAM and 1GB of persistent storage. Once you have activated your free OpenShift Online Starter subscription, your account will be provisioned in seconds. Refresh the page and open the web console for OpenShift.

On the top right-hand side of the console, click **Create Project**. The name is the only required field. You can call it project.

To deploy our previously created image, click **Deploy image**. This will open a wizard that allows you to provide the name of the image pushed to Docker Hub. After you type the name of the image including in the format /refcard-demo, click the magnifier icon so OpenShift can read the metadata of the image. Now, click the blue **Deploy** button.

The image will be downloaded, and a new container instance will be executed based on your image.

![]({{site.cdn}}/webservices/docker/docker-scaleup-in-cloud.png)

The up and down arrows control the number of replicas. Because we are running with a free subscription, scaling to more than two replicas will exceed the usage memory quota of 1GB and no replicas will be created. However, this feature can give you an idea of how easy is to create multiple container replicas and scale your application.
