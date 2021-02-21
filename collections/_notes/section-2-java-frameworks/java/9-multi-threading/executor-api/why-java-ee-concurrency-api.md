---
layout: post
title: Why Java EE Concurrency API
permalink: /:collection/java/multithreading/why-java-ee-concurrency-api
---


# Why?
- Every Java Enterprise application always works within an application server, the underlying container, and these containers provide runtime support for application components like Enterprise Java Beans and servlets.
- Very often, Java Enterprise servers provide central resource management, resources like JDBC data sources, transaction management, connection pooling, et cetera.  So, there is this managed environment that is set up by the container, and in such an environment, application integrity is very important.
- it is required that the contextual information of the container is provided to the thread. Contextual information is Java namingand directory interface naming, class loader information, security context. It is very important that the container propagates this information to all the threads executing the jobs for you. 
- If we try to create our own threads using the Java Standard Edition platform, then the container will not be aware or wouldn't have any knowledge of these thread resources, that's exactly why the Java Enterprise Edition concurrency utilities were born.

# Good to Know Java EE Terms

- **JNDI** - Java Naming and Directory Interface is an API in Java to access data tree services. It'll help you to look up data and resources by means of a name and that name is a JNDI name. It'll help you to look up data and resources by means of a name and that name is a JNDI name.
- **Stateless session bean** - This is a type of an Enterprise Java bean which is used to perform independent operations. As the name suggests, it is stateless which means it does not conserve any state of the client. However, yes, it can of course, have its own state present with it. The application server often creates a pool of such stateless session beans so that it can do the request processing operations on those business methods.
- Global transactions – XA Resource for Resource Managers. 
	- When you have a distributed environment, you may have multiple resource managers on which you are trying to do transactions. So those multiple resources could be databases or JMS queues or application servers etc. 
	- XA or extended architecture,is an open standard which is defined for executing a global transaction that accesses more than one backend data tool. 
	- This is the one which will help you define the interactions between the transaction manager and the resource manager. The goal of XA is to allow multiple resources like Database, JMS queues, transactional caches, etc., to be accessed within the same transaction thereby preserving the ACID properties across applications.
- Java transaction API (JTA) – Interfaces for Transaction Mangement.
	- Basically a list of interfaces between a transaction manager and the parties involved in the transaction. 
	- This transaction API has specifications to perform transactions over a distributed network. 
	- The parties involved in transaction processing will be the resource manager, application server, and code.
