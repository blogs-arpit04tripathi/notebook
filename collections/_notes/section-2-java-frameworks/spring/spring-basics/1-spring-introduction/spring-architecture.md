---
layout: post
title: Spring Framework Architecture
permalink: /:collection/spring/architecture
---

As of Spring 4.0, there are 20 distinct modules in the Spring Framework distribution, with three JAR files for each module (the binary class library, the source JAR file, and a JavaDoc JAR file).

![]({{site.cdn}}/spring/spring-core/spring-framework-architecture.png)

|Core Container||
|---|---|
|Core |	provides the fundamental parts of the framework, including the IoC and DI features.|
|Bean |	provides BeanFactory, which is a sophisticated implementation of the factory pattern.|
|Context |	builds on the solid base provided by the Core and Beans modules and it is a medium to access any objects defined and configured. The ApplicationContext interface is the focal point of the Context module.|
|SpEL |	provides a powerful expression language for querying and manipulating an object graph at runtime.|

In addition to the bean factory and application context, this module also supplies many enterprise services such as email, JNDI access, EJB integration, and scheduling.

|Data Access/Integration||
|---|---|
|JDBC |	Provides a JDBC-abstraction layer that removes the need for tedious JDBC related coding.|
|ORM |	Provides integration layers for popular object-relational mapping APIs, including JPA, JDO, Hibernate, and iBatis.|
|OXM |	Provides an abstraction layer that supports Object/XML mapping implementations for JAXB, Castor, XMLBeans, JiBX and XStream.|
|JMS |	Contains features for producing and consuming messages.|
|Transaction |	Supports programmatic and declarative transaction management for classes that implement special interfaces and for all your POJOs.|
	
|Web||
|---|---|
|Web|	Provides basic web-oriented integration features such as multipart file-upload functionality and the initialization of the IoC container using servlet listeners and a web-oriented application context.|
|Web-MVC |	Contains Spring's Model-View-Controller (MVC) implementation for web applications.|
|Web-Socket |	Provides support for WebSocket-based, two-way communication between the client and the server in web applications.|
|Web-Portlet |	Provides the MVC implementation to be used in a portlet environment and mirrors the functionality of Web-Servlet module.|

|Miscellaneous||
|---|---|
|AOP |	Provides an aspect-oriented programming implementation allowing you to define method-interceptors and pointcuts to cleanly decouple code that implements functionality that should be separated.|
|Aspects| 	Provides integration with AspectJ, which is again a powerful and mature AOP framework.|
|Instrumentation |	Provides class instrumentation support and class loader implementations to be used in certain application servers.|
|Messaging |	Provides support for STOMP as the WebSocket sub-protocol to use in applications. It also supports an annotation programming model for routing and processing STOMP messages from WebSocket clients.|
|Test |	Supports the testing of Spring components with JUnit or TestNG frameworks.|