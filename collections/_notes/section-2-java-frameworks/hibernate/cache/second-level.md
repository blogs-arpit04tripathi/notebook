---
layout: post
title: Second Level Cache
permalink: /:collection/hibernate/cache/second-level
---

**Fist level cache**: This is enabled by default and works in session scope.

**Second level cache**: This is apart from first level cache which is available to be used globally in session factory scope.

![]({{site.cdn}}/hibernate/cache.png)

-	Above statement means, **second level cache is created in session factory scope** and is **available to be used in all sessions** which are created using that particular session factory.
-	It also means that **once session factory is closed, all cache associated with it die** and cache manager also closed down.
Further, It also means that if you have two instances of session factory (normally no application does that), you will have two cache managers in your application and while accessing cache stored in physical store, you might get unpredictable results like cache-miss.

**How to configure Hibernate Second Level Cache using EHCache?**
-	EHCache is the best choice for utilizing hibernate second level cache. 
-	Following steps are required to enable EHCache in hibernate application.
