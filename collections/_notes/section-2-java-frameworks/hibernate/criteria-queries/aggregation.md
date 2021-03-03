---
layout: post
title: projections and aggregates
permalink: /:collection/hibernate/hql/criteria/aggregation
---

Instead of working with objects from the result set, you can treat the results from the result set as a set of rows and columns, also known as a projection of the data. This is similar to how you would use data from a SELECT query with JDBC.

# Single Aggregate ( Getting Row Count )

```java
Criteria crit = session.createCriteria(Product.class);
crit.setProjection(Projections.rowCount());
List<Long> results = crit.list();
```

-	avg(String propertyName): Gives the average of a property’s value
-	count(String propertyName): Counts the number of times a property occurs
-	countDistinct(String propertyName): Counts the number of unique values the property contains
-	max(String propertyName): Calculates the maximum value of the property values
-	min(String propertyName): Calculates the minimum value of the property values
-	sum(String propertyName): Calculates the sum total of the property values

# Multiple Aggregates

```java
Criteria crit = session.createCriteria(Product.class);
ProjectionList projList = Projections.projectionList();
projList.add(Projections.max("price"));
projList.add(Projections.min("price"));
projList.add(Projections.avg("price"));
projList.add(Projections.countDistinct("description"));
crit.setProjection(projList);
List<object[]> results = crit.list();
```

# Getting Selected Columns

Another use of projections is to retrieve individual properties, rather than entities.

```java
Criteria crit = session.createCriteria(Product.class);
ProjectionList projList = Projections.projectionList();
projList.add(Projections.property("name"));
projList.add(Projections.property("description"));
crit.setProjection(projList);
crit.addOrder(Order.asc("price"));
List<object[]> results = crit.list();
```
