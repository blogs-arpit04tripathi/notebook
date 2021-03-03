---
layout: post
title: Basic Restrictions
permalink: /:collection/hibernate/hql/criteria/basic-restrictions
---

# equals
```java
Criteria crit = session.createCriteria(Product.class);
crit.add(Restrictions.eq("description","Mouse"));
List<Product> results = crit.list();
```

# not equal to
```java
Criteria crit = session.createCriteria(Product.class);
crit.add(Restrictions.ne("description","Mouse"));
List<Product> results = crit.list();
```

You cannot use the not-equal restriction to retrieve records with a NULL value in the database for that property (in SQL, and therefore in Hibernate, NULL represents the absence of data, and so cannot be compared with data). If you need to retrieve objects with NULL properties, you will have to use the isNull() restriction.

# isNull and isNotNull
```java
Criteria crit = session.createCriteria(Product.class);
crit.add(Restrictions.isNull("name"));
crit.add(Restrictions.isNotNull("name"));
List<Product> results = crit.list();
```

# gt, ge, lt, le
```java
Criteria crit = session.createCriteria(Product.class);
crit.add(Restrictions.gt("price", 25.0));
List<Product> results = crit.list();
```

# like
```java
Criteria crit = session.createCriteria(Product.class);
crit.add(Restrictions.like("name","Mou%",MatchMode.ANYWHERE));
List<Product> results = crit.list();
```

-	ANYWHERE: Anyplace in the string
-	END: The end of the string
-	EXACT: An exact match
-	START: The beginning of the string
