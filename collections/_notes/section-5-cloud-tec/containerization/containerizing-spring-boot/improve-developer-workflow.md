---
layout: post
title: Improving the Developer Workflow
permalink: /:collection/containerization/docker/improve-developer-workflow
---

As developer, to place your application in the cloud, you had to follow these steps:
-	Create your application.
-	Create a Dockerfile.
-	Create a Docker image.
-	Deploy the image on OpenShift.
-	Create a service to act as a load balancer.
-	Create a router.

What if I told you that OpenShift has a feature called S2I (source-to-image) that allows your application to be containerized and deploy from the sources? Your application’s source code just needs to be accessible in a Git repository on the internet.

If you don’t want to create a repository from the scratch for this application, just fork my repository.

Before exploring the S2I features, we need first to get rid of all objects that have been created up until now (deployment, route, service, etc.). The easiest way to do this is by deleting the entire project.

To delete the entire project, select **View all projects** in the top left corner. In the **My projects** screen, select your application menu and click **Delete Project**. You will be asked to confirm the deletion of the project.

![]({{site.cdn}}/webservices/docker/docker-create-new-project.png)

Create your project again. If you receive a message saying that your project already exists, wait a few seconds and try again. The project may still be being removed from the cluster.

In **Get started with your project**, instead of deploying an image as we did previously, click **Browse Catalog**. The OpenShift catalog has support for several languages, databases, and middleware runtimes. You can just go to the **Java** tab and select **OpenJDK 8**.

In the wizard, make sure to fill the following fields:
-	**Application name**: refcard-demo
-	**Custom HTTP route hostname**:
-	**Git repository URL**: Use your forked repository from [here](https://github.com/rafabene/refcard-demo).
-	**Git reference (git branch)**: Master
-	**Context directory**: (Delete the existing value)
Click Create.

![]({{site.cdn}}/webservices/docker/create-new-openjdk-config.png)

The build process will start automatically. You can check the build log running in the **Overview** page and note that OpenShift will clone your Git repository and run a Maven package on your project. When the build process completes, the new container will be deployed automatically.

You can notice also that the route and service objects were automatically created.
