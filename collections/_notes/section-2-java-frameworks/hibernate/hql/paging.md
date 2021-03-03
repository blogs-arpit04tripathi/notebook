---
layout: post
title: HQL – Paging Through the ResultSet
permalink: /:collection/hibernate/hql/paging
---

```java
Query query = session.createQuery("from Product");
query.setFirstResult(1);
query.setMaxResults(2);
List results = query.list();
displayProductsList(results);
```
