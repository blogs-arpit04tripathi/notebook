---
layout: post
title: EE Concurrency API
permalink: /:collection/java/multithreading/ee-concurrency-api
---


- **ManagedThreadFactory** – Mostly referenced by @Resource(lookup=”jndi/name”) for field.
- **ManagedExecutorService**
- **ManagedScheduledExecutorService**
- **ContextService** – For Contextual proxies.

- Ways to use environment references of managed resources:
	- Declare in deployment descriptor.
	- look it up in the container or the environment or the network through ***Java Naming and Directory Interface API***. Java Naming and Directory Interfaces is an API in Java which is used to access directory services.
- Additionally, tasks could also optionally implement **ManagedTask** and even register **ManagedTaskListener** to receive lifecycle notifications.
- **ManagedTask** interface is actually used to provide identifying information about the task or maybeto provide additional execution properties.
- **ManagedTaskListener** is basically a listener class used to receive lifecycle notifications - track the stateof your task's future. So whenever the state changes, you can configure this listener and whatever you want as a part of the processing.
- For Example, Glassfish server has Glassfish console with default Concurrent Resources.
- all the four main services that we see, the managed executor, managed scheduled executor, managed thread factory and contact service, these are the interfaces that the specification of JSR has. But, the implementation classes for these are going to be provided by the underlying application server that you are using. In our case, it is GlassFish server, And whenever you are going to change your server, let's say you tomorrow are working on JBoss or maybe WildFly, then these implementation classes will change according to the underlying provider.
- **ManagedScheduledExecutorService** is fetched by jndi lookup name. **shutdown()** not allowed on managed resources.
- Dependency in maven - javax:javaee-api and c3p0

# USE CASE
- Read bank Account Details for all users
- Get All Transaction information and save to file.

![managed-executor-service-usecase]({{site.cdn}}/java/multi-threading/managed-executor-service-usecase.png)

- DataSource object is used here with c3 pooling.
- Datasource.getConnection() gives the connection object.
