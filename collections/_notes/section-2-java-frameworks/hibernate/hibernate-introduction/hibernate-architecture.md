---
layout: post
title: Hibernate Architecture
permalink: /:collection/hibernate/architecture
---

![]({{site.cdn}}/hibernate/hibernate-architecture.png)

![]({{site.cdn}}/hibernate/)

**Name some important interfaces of Hibernate framework?**  
1. **SessionFactory (org.hibernate.SessionFactory)**
SessionFactory is an immutable thread-safe cache of compiled mappings for a single database. We need to initialize SessionFactory once and then we can cache and reuse it. SessionFactory instance is used to get the Session objects for database operations.

2. **Session (org.hibernate.Session)**
Session is a single-threaded, short-lived object representing a conversation between the application and the persistent store. It wraps JDBC java.sql.Connection and works as a factory for org.hibernate.Transaction. We should open session only when it’s required and close it as soon as we are done using it. Session object is the interface between java application code and hibernate framework and provide methods for CRUD operations.

3. **Transaction (org.hibernate.Transaction)**
Transaction is a single-threaded, short-lived object used by the application to specify atomic units of work. It abstracts the application from the underlying JDBC or JTA transaction. A org.hibernate.Session might span multiple org.hibernate.Transaction in some cases.

# Hibernate Interfaces

![]({{site.cdn}}/hibernate/hibernate-interfaces.png)
