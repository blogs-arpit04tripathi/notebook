---
layout: post
title: Native SQL
permalink: /:collection/hibernate/queries/native-sql
---

-	Writing the query in DB specific Query Language is called Native SQL.
-	After you pass a string containing the SQL query to the createSQLQuery() method, you should associate the SQL result with an existing Hibernate entity, a join, or a scalar result. The SQLQuery interface has addEntity(), addJoin(), and addScalar() methods.

```java
String sql = "select avg(product.price) as avgPrice from Product product";
SQLQuery query = session.createSQLQuery(sql);
query.addScalar("avgPrice",Hibernate.DOUBLE);
List results = query.list();
```
```java
String sql = "select {supplier.*} from Supplier supplier";
SQLQuery query = session.createSQLQuery(sql);
query.addEntity("supplier", Supplier.class);
List results = query.list();
 
//Hibernate modifies the SQL and executes the following command against the database:
select Supplier.id as id0_, Supplier.name as name2_0_ from Supplier supplier
```
