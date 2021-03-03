---
layout: post
title: Spring Cloud Bus
permalink: /:collection/microservices/spring-cloud-bus
---

**What is Spring Cloud Bus? Need for it?**

![]({{site.cdn}}/webservices/microservices/spring-cloud-bus.png)

Consider the scenario that we have multiple applications reading the properties using the Spring Cloud Config and the Spring Cloud Config in turn reads these properties from GIT.

Consider the below example where multiple employee producer modules are getting the property for Eureka Registration from Employee Config Module. 

What will happen if suppose the eureka registration property in GIT changes to point to another Eureka server. In such a scenario we will have to restart the services to get the updated properties. There is another way of using Actuator Endpoint **/refresh**. But we will have to individually call this url for each of the modules. 

For example if Employee Producer1 is deployed on port 8080 then call **http://localhost:8080/refresh**. Similarly for Employee Producer2 **http://localhost:8081/refresh** and so on. This is again cumbersome. This is where Spring Cloud Bus comes into picture. 

The Spring Cloud Bus provides feature to refresh configurations across multiple instances. So in above example if we refresh for Employee Producer1, then it will automatically refresh for all other required modules. This is particularly useful if we are having multiple microservice up and running. This is achieved by connecting all microservices to a single message broker. Whenever an instance is refreshed, this event is subscribed to all the microservices listening to this broker and they also get refreshed. The refresh to any single instance can be made by using the endpoint **/bus/refresh**.

**What is Spring Cloud Bus? Need for it?**  
Consider the scenario that we have multiple applications reading the properties using the Spring Cloud Config and the Spring Cloud Config in turn reads these properties from GIT.

Consider the below example where multiple employee producer modules are getting the property for Eureka Registration from Employee Config Module. 
