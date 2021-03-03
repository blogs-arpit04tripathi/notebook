---
layout: post
title: HQL Named Parameters
permalink: /:collection/hibernate/hql/named-params
---

```java
String hql = "from Product where price > :price";
Query query = session.createQuery(hql);
query.setDouble("price",25.0);
List results = query.list();
```

