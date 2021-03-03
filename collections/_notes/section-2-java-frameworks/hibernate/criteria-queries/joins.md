---
layout: post
title: perform associations (joins)
permalink: /:collection/hibernate/hql/criteria/joins
---

The association works when going from **either one-to-many or from many-to-one.** First, we will demonstrate how to use one-to-many associations to obtain suppliers who sell products with a price over $25. Notice that we create a new Criteria object for the products property, add restrictions to the products’ criteria we just created, and then obtain the results from the supplier Criteria object.

```java
Criteria crit = session.createCriteria(Supplier.class);
Criteria prdCrit = crit.createCriteria("products");
prdCrit.add(Restrictions.gt("price",25.0));
List results = crit.list();
```

Going the other way, we obtain all the products from the supplier MegaInc using many-to-one associations:

```java
Criteria crit = session.createCriteria(Product.class);
Criteria suppCrit = crit.createCriteria("supplier");
suppCrit.add(Restrictions.eq("name","Hardware Are We"));
List results = crit.list();
```

