---
layout: post
title: Hibernate - Misc
permalink: /:collection/hibernate/misc
---

**What is the benefit of Hibernate Tools Eclipse plugin?**  
Hibernate Tools plugin helps us in writing hibernate configuration and mapping files easily. The major benefit is the content assist to help us with properties or xml tags to use. It also validates them against the Hibernate DTD files, so we know any mistakes before hand. 
> (Learn how to install and use at [Hibernate Tools Eclipse Plugin](http://www.journaldev.com/2940/hibernate-tools-eclipse-plugin).)

**Which design patterns are used in Hibernate framework?**  
Some of the design patterns used in Hibernate Framework are:
-	Domain Model Pattern – An object model of the domain that incorporates both behavior and data.
-	Data Mapper – A layer of Mappers that moves data between objects and a database while keeping them independent of each other and the mapper itself.
-	[Proxy Pattern]( http://www.journaldev.com/1572/proxy-design-pattern) for lazy loading
-	[Factory pattern]( http://www.journaldev.com/1392/factory-design-pattern-in-java) in SessionFactory

**Why we are using JPA Annotation instead of Hibernate ? For example, why we are not using this org.hibernate.annotations.Entity?**
- JPA is a standard specification. Hibernate is an implementation of the JPA specification.
- Hibernate implements all of the JPA annotations.
- The Hibernate team recommends the use of JPA annotations as a best practice.

**What are best practices to follow with Hibernate framework?**  
Some of the best practices to follow in Hibernate are:
-	Always check the primary key field access, if it’s generated at the database layer then you should not have a setter for this.
-	By default hibernate set the field values directly, without using setters. So if you want hibernate to use setters, then make sure proper access is defined as @Access(value=AccessType.PROPERTY).
-	If access type is property, make sure annotations are used with getter methods and not setter methods. Avoid mixing of using annotations on both filed and getter methods.
-	Use native sql query only when it can’t be done using HQL, such as using database specific feature.
-	If you have to sort the collection, use ordered list rather than sorting it using Collection API.
-	Use named queries wisely, keep it at a single place for easy debugging. Use them for commonly used queries only. For entity specific query, you can keep them in the entity bean itself.
-	For web applications, always try to use JNDI DataSource rather than configuring to create connection in hibernate.
-	Avoid Many-to-Many relationships, it can be easily implemented using bidirectional One-to-Many and Many-to-One relationships.
-	For collections, try to use Lists, maps and sets. Avoid array because you don’t get benefit of lazy loading.
-	Do not treat exceptions as recoverable, roll back the Transaction and close the Session. If you do not do this, Hibernate cannot guarantee that in-memory state accurately represents the persistent state.
-	Prefer DAO pattern for exposing the different methods that can be used with entity bean
-	Prefer lazy fetching for associations

**How to integrate log4j logging in hibernate application?**  
Hibernate 4 uses JBoss logging rather than slf4j used in earlier versions. For log4j configuration, we need to follow below steps.
-	Add log4j dependencies for maven project, if not maven then add corresponding jar files.
-	Create log4j.xml configuration file or log4j.properties file and keep it in the classpath. You can keep file name whatever you want because we will load it in next step.
-	For standalone projects, use static block to configure log4j using `DOMConfigurator` or `PropertyConfigurator`. For web applications, you can use ServletContextListener to configure it.
That’s it, our setup is ready. Create `org.apache.log4j.Logger` instance in the java classes and start logging. 

> (For complete example code, you should go through [Hibernate log4j example]( http://www.journaldev.com/2984/hibernate-log4j-logging) and [Servlet log4j example]( http://www.journaldev.com/1997/servlet-jdbc-database-connection-example).)

**How to use application server JNDI DataSource with Hibernate framework?**  
For web applications, it’s always best to allow servlet container to manage the connection pool. That’s why we define JNDI resource for DataSource and we can use it in the web application. It’s very easy to use in Hibernate, all we need is to remove all the database specific properties and use below property to provide the JNDI DataSource name.

```xml
<property name="hibernate.connection.datasource">java:comp/env/jdbc/MyLocalDB</property>
```

> (For a complete example, go through [Hibernate JNDI DataSource Example]( http://www.journaldev.com/2905/hibernate-tomcat-jndi-datasource-example-tutorial).)

**How to integrate Hibernate and Spring frameworks?**  
Spring is one of the most used Java EE Framework and Hibernate is the most popular ORM framework. That’s why Spring Hibernate combination is used a lot in enterprise applications. The best part with using Spring is that it provides out-of-box integration support for Hibernate with Spring ORM module. Following steps are required to integrate Spring and Hibernate frameworks together.
-	Add hibernate-entitymanager, hibernate-core and spring-orm dependencies.
-	Create Model classes and corresponding DAO implementations for database operations. Note that DAO classes will use SessionFactory that will be injected by Spring Bean configuration.
-	If you are using Hibernate 3, you need to configure `org.springframework.orm.hibernate3.LocalSessionFactoryBean` or `org.springframework.orm.hibernate3.annotation.AnnotationSessionFactoryBean` in Spring Bean configuration file. For Hibernate 4, there is single class `org.springframework.orm.hibernate4.LocalSessionFactoryBean` that should be configured.
-	Note that we don’t need to use Hibernate Transaction Management, we can leave it to Spring declarative transaction management using `@Transactional` annotation.

> (For complete example go through [Spring Hibernate Integration]( http://www.journaldev.com/3524/spring-hibernate-integration-example-tutorial) and [Spring MVC Hibernate Integration]( http://www.journaldev.com/3531/spring-mvc-hibernate-mysql-integration-crud-example-tutorial).)
