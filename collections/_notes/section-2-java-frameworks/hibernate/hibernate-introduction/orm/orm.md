---
layout: post
title: ORM (Object Relational Mapping)
permalink: /:collection/hibernate/orm
---

-	Object-Relational Mapping (ORM) 
-	Programming technique for converting data between relational DB and OOP languages such as Java, C# etc. 
-	Used in Data Layer of application
-	Implements JPA

JPA implementation follows the rules set by JPA specifications so that if in future, we want to use some other provider (Not Hibernate) which implements JPA, we can do it with minimal changes.

An ORM solution consists of the following four entities:
-	An API to perform basic CRUD operations on objects of persistent classes.
-	A language or API to specify queries that refers to classes and properties of classes.
-	A configurable facility for specifying mapping metadata.
-	A technique to interact with transactional objects to perform dirty checking, lazy association fetching, and other optimization functions.
