---
layout: post
title: sqlRestriction()
permalink: /:collection/hibernate/hql/criteria/sql-restriction
---

sqlRestriction() restriction allows you to directly specify SQL in the Criteria API. It’s useful if you need to use SQL clauses that Hibernate does not support through the Criteria API.

```java
Criteria crit = session.createCriteria(Product.class);
crit.add(Restrictions.sqlRestriction("{alias}.description like 'Mou%'"));
List<Product> results = crit.list();
```
