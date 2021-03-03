---
layout: post
title: POJO vs Java Beans vs EJB
permalink: /:collection/spring/core/pojo-bean-ejb
---

# POJO (Plain Old Java Object) 
- Ordinary Java Object, not a special object.
- POJO should not have to
  - Extend prespecified classes, as in public class Foo extends javax.servlet.http.HttpServlet { ...
  - Implement prespecified interfaces, as in public class Bar implements javax.ejb.EntityBean { ...
  - Contain prespecified annotations, as in @javax.ejb.Entity public class Baz{ ...

# JavaBean
-	reusable software components that can be injected by IOC container.
-	They are used to encapsulate many objects into a single object (the bean), so that they can be passed around as a single bean object instead of as multiple individual objects. 
-	must obey certain conventions
    -	public default no-argument constructor.
    -	accessor methods and mutator methods, following a standard naming convention.
    -	class should be serializable.

# EJB (Enterprise JavaBean)
-	They are some objects whose life cycle is managed by a container (the EJB container), so you don’t “new Xxxx()” them - instead you “request” for an instance and who offer certain out of the box functionalities, like security, transactionality, persistence (although in newer versions of EJB the persistence part became a separate standard - JPA), thread-safety, remote-calling, etc.
-	They only reside in application servers that handle EJBs (Tomcat doesn't hold EJBs). There are 3 types of EJBs:
  -	**Session**: Usually contain some business logic.
  -	**Entity**: Usually interface with a data store, such as a database.
  -	**Message-Driven**: Receives messages from JMS.