---
layout: post
title: Making Your Cloud Application Accessible Externally
permalink: /:collection/containerization/docker/make-application-accessible-externally
---

At this moment, your application is being executed inside the cluster, but it’s not accessible externally.

Because we can have more than one container executing, we need to create a load balancer to receive requests to this application. This load balancer is known as a “service” in the Kubernetes world. Kubernetes services can be created through a command line tool or using YAML or JSON format.

To avoid the installation of any command line tool, you can import the following YAML file by clicking **Add to project** on the top right-hand side of the screen and selecting **Import YAML/JSON**.  
This file can also be copied from here.
```
kind: Service
apiVersion: v1
metadata:
 name: myservice
spec:
 type: LoadBalancer
 ports:
   - port: 8080 
 selector: 
  app: refcard-demo
```
This file requests the OpenShift/Kubernetes cluster creates a load balancer for the application called *refcard-demo* on port 8080. After defining this Kubernetes service, you will notice that a new section called **Networking** is available in your application. Although the Kubernetes service acts as a load balancer for internal traffic, we need an extra step to make our application available externally. To allow external access, we need to create a route. Click **Create Route**.

![]({{site.cdn}}/webservices/docker/docker-create-route.png)

In the **Create Route** screen, accept the default values and click the blue **Create** button. Now, on the **Overview** screen, there’s a route to your application. You can click on the route link to open the application address in another tab. Don’t forget to add /api/hello in the address to allow it to access the endpoint that we have previously created (http:///api/hello).
