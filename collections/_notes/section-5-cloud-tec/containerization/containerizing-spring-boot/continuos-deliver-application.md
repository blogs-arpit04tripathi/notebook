---
layout: post
title: Continuously Delivering Your Java Application
permalink: /:collection/containerization/docker/continuos-deliver-application
---

Since you created your application from the source code, OpenShift also shows the commit version that was used to create your application.

![]({{site.cdn}}/webservices/docker/containers-created.png)

You can enable the continuous delivery of your code by configuring GitHub to send notifications of new commits to OpenShift. When OpenShift receives that notification, it will start the build automatically.

Click the **Build** link, as you can see in the image above. That will take you to **Build Configuration**. In the **Configuration** tab, you can copy the GitHub webhook URL (located on the right-hand side of the screen under the **Triggers** section).

![]({{site.cdn}}/webservices/docker/builds-config-dashboard.png)

Copy the GitHub webhook URL. Open your GitHub project settings. Click **Add webhook** and fill the web form the following values:
-	**Payload URL**:
-	**Content type**:
-	**Secret**:
-	**SSL verification**:
-	**Which events would you like to trigger this webhook?**: Just the push event.
-	**Active**:

![]({{site.cdn}}/webservices/docker/add-github-webhook.png)

Click the green **Add webhook** button. To test the continuous delivery, you can modify the file HelloController.java. Change, for example, the RESPONSE_STRING_FORMAT variable from Hello from ‘%s’: %dto Version 2 - Hello from ‘%s’: %d.

When you push the committed change to your GitHub repository, GitHub will notify OpenShift and Build #2 will start automatically.

![]({{site.cdn}}/webservices/docker/build-running.png)

At the end of the build, OpenShift will replace all the running replicas with the one containing your changes. At the end of the deployment, you can open your browser at http:///api/hello and you should see the prefix Version 2.
