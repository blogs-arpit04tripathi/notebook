---
layout: post
title: Obtain unique result
permalink: /:collection/hibernate/hql/criteria/unique-result
---

-	Sometimes you know you are going to return only zero or one object from a given query. This could be because you are calculating an aggregate or because your restrictions naturally lead to a unique result. 
-	If you want obtain a single Object reference instead of a List, the uniqueResult() method on the Criteria object returns an object or null. If there is more than one result, the uniqueResult() method throws a HibernateException.
-	The following short example demonstrates having a result set that would have included more than one result, except that it was limited with the setMaxResults() method:

```java
Criteria crit = session.createCriteria(Product.class);
Criterion price = Restrictions.gt("price",new Double(25.0));
crit.setMaxResults(1);
Product product = (Product) crit.uniqueResult();
```
