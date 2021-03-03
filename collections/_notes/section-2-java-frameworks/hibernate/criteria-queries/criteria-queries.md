---
layout: post
title: Criteria Queries
permalink: /:collection/hibernate/hql/criteria-queries
---

The criteria query API lets you build nested, structured query expressions in Java, providing a compile-time syntax checking that is not possible with a query language like HQL or SQL.

The Criteria API also includes **query by example (QBE)** functionality. This lets you supply example objects that contain the properties you would like to retrieve instead of having to step-by-step spell out the components of the query. It also includes projection and aggregation methods, including count().

-	Criteria API allows you to build up a criteria query object programmatically; the org.hibernate.Criteria interface defines the available methods for one of these objects. 
-	Hibernate Session interface contains several overloaded createCriteria()methods.
-	Pass the persistent object’s class or its entity name to the createCriteria() method, and hibernate will create a Criteria object that returns instances of the persistence object’s class when your application executes a criteria query.

```java
Criteria crit = session.createCriteria(Product.class);
List<Product> results = crit.list();
```
