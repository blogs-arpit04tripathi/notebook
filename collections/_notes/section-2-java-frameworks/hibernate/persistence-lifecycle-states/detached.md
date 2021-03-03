---
layout: post
title: Detached Object
permalink: /:collection/hibernate/persistence/detached
---

![]({{site.cdn}}/hibernate/detached-object.png)


-	Detached objects have a representation in the database, but changes to the object will not be reflected in the database, and vice-versa. This temporary separation of the object and the database is shown in image below.
-	A detached object can be created by closing the session that it was associated with, or by evicting it from the session with a call to the session’s evict() method.

One reason you might consider doing this would be to read an object out of the database, modify the properties of the object in memory, and then store the results some place other than your database. This would be an alternative to doing a deep copy of the object.

In order to persist changes made to a detached object, the application must reattach it to a valid Hibernate session. A detached instance can be associated with a new Hibernate session when your application calls one of the load, refresh, merge, update(), or save() methods on the new session with a reference to the detached object. After the call, the detached object would be a persistent object managed by the new Hibernate session.

