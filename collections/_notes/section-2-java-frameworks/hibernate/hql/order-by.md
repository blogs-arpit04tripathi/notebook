---
layout: post
title: HQL – Sorting Results with the ‘order by’ clause
permalink: /:collection/hibernate/hql/order-by
---

```java
from Product p where p.price>25.0 order by p.price desc
//from Product p order by p.supplier.name asc, p.price asc

select s.name, p.name, p.price from Product p inner join p.supplier as s
//from Product p inner join p.supplier as s
```
