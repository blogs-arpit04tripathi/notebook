---
layout: post
title: Transient Object
permalink: /:collection/hibernate/persistence/transient
---

![]({{site.cdn}}/hibernate/transient-object.png)

-	Transient objects exist in heap memory. Hibernate does not manage transient objects or persist changes to transient objects.
- To persist the changes to a transient object, you would have to ask the session to save the transient object to the database, at which point Hibernate assigns the object an identifier and marks the object as being in persistent state.
