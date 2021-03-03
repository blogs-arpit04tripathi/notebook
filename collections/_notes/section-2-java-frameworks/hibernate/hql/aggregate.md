---
layout: post
title: HQL Aggregate Methods
permalink: /:collection/hibernate/hql/aggregate
---

```java
Select count(*) from Product product
```

The aggregate functions available through HQL include the following:
1.	**avg(property name)**: The average of a property’s value
2.	**count(property name or *)**: The number of times a property occurs in the results
3.	**max(property name)**: The maximum value of the property values
4.	**min(property name)**: The minimum value of the property values
5.	**sum(property name)**: The sum total of the property values
