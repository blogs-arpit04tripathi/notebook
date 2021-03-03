---
layout: post
title: paging through the result set
permalink: /:collection/hibernate/hql/criteria/paging
---

setFirstResult() method takes an integer that represents the first row in your result set, starting with row 0. 
```java
Criteria crit = session.createCriteria(Product.class);
crit.setFirstResult(1);
crit.setMaxResults(20);
List<Product> results = crit.list();
```
