---
layout: post
title: First Level Cache
permalink: /:collection/hibernate/cache/first-level
---

![]({{site.cdn}}/hibernate/cache-level-1.png)

```java
//Open the hibernate session
Session session = HibernateUtil.getSessionFactory().openSession();
session.beginTransaction();
 
//fetch the department entity from database first time
DepartmentEntity department = (DepartmentEntity) session.load(DepartmentEntity.class, new Integer(1));
System.out.println(department.getName());
 
//fetch the department entity again
department = (DepartmentEntity) session.load(DepartmentEntity.class, new Integer(1));
System.out.println(department.getName());
 
session.getTransaction().commit();
HibernateUtil.shutdown();
```

Here, second "session.load()" statement does not execute select query again and load the department entity directly.

But if we use 2 different session objects to load, then, both the time retrieval will happen.
-	We can use session evict() method to remove a single object from the hibernate first level cache.
-	We can use session clear() method to clear the cache i.e delete all the objects from the cache.
-	We can use session contains() method to check if an object is present in the hibernate cache or not, if the object is found in cache, it returns true or else it returns false.
-	Since hibernate cache all the objects into session first level cache, while running bulk queries or batch updates it’s necessary to clear the cache at certain intervals to avoid memory issues.
