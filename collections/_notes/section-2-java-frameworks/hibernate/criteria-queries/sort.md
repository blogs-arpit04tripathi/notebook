---
layout: post
title: sort query results
permalink: /:collection/hibernate/hql/criteria/sort
---

```java
Criteria crit = session.createCriteria(Product.class);
crit.add(Restrictions.gt("price",10.0));
crit.addOrder(Order.desc("price"));
List<Product> results = crit.list();
```

You may add more than one Order object to the Criteria object. Hibernate will pass them through to the underlying SQL query. Your results will be sorted by the first order, then any identical matches within the first sort will be sorted by the second order, and so on. Beneath the covers, **Hibernate passes this on to an SQL ORDER BY clause after substituting the proper database column name for the property.**
