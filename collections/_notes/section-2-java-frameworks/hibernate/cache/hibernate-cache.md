---
layout: post
title: Hibernate Cache
permalink: /:collection/hibernate/cache
---

Hibernate Cache can be very useful in gaining fast application performance if used correctly. 
The idea behind cache is to reduce the number of database queries, hence reducing the throughput time of the application.

**First Level Cache**
-	Hibernate first level cache is associated with the Session object. 
-	enabled by default and there is no way to disable it. However, hibernate provides methods through which we can delete selected objects from the cache or clear the cache completely.
-	Any object cached in a session will not be visible to other sessions and when the session is closed, all the cached objects will also be lost.

**Second Level Cache**
-	Hibernate Second Level cache is disabled by default but we can enable it through configuration. 
-	Currently EHCache and Infinispan provides implementation for Hibernate Second level cache and we can use them.

**Query Cache**
-	Hibernate can also cache result set of a query. 
-	Hibernate Query Cache doesn’t cache the state of the actual entities in the cache; it caches only identifier values and results of value type. So, it should always be used in conjunction with the second-level cache.

**What is Query Cache in Hibernate?**  
Hibernate implements a cache region for queries resultset that integrates closely with the hibernate second-level cache. This is an optional feature and requires additional steps in code. This is only useful for queries that are run frequently with the same parameters. First of all we need to configure below property in hibernate configuration file.

```xml
<property name="hibernate.cache.use_query_cache">true</property>
```
And in code, we need to use setCacheable(true) method of Query, quick example looks like below.

```java
Query query = session.createQuery("from Employee");
query.setCacheable(true);
query.setCacheRegion("ALL_EMP");
```
