---
layout: post
title: obtain distinct results
permalink: /:collection/hibernate/hql/criteria/distinct
---

```java
Criteria crit = session.createCriteria(Product.class);
Criterion price = Restrictions.gt("price",new Double(25.0));
crit.setResultTransformer( DistinctRootEntityResultTransformer.INSTANCE )
List<Product> results = crit.list();
```

**Rather than using SELECT DISTINCT with SQL, the distinct result transformer compares each of your results using their default hashCode() methods, and only adds those results with unique hash codes to your result set.** This may or may not be the result you would expect from an otherwise equivalent SQL DISTINCT query, so **be careful with this.**

An additional performance note: the comparison is done in Hibernate’s Java code, not at the database, so non-unique results will still be transported across the network.
