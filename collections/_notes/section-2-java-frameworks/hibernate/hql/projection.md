---
layout: post
title: HQL select clause and projection
permalink: /:collection/hibernate/hql/projection
---


If you want to obtain the properties of objects in the result set, use the select clause. For instance, we could run a projection query on the products in the database that only returned the names, instead of loading the full object into memory, as follows:

```sql
select product.name from Product product
```

Additionally, we can retrieve the prices and the names for each product in the database, like so:

```sql
select product.name, product.price from Product product
```

If you’re only interested in a few properties, this approach can allow you to reduce network traffic to the database server and save memory on the application’s machine.
