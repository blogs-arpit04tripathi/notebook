---
layout: post
title: Entity / Persistence LifeCycle States
permalink: /:collection/hibernate/persistence/lifecycle
---

**What are different states of an entity bean?**  
An entity bean instance can exist is one of the three states.
-	**Transient**: When an object is never persisted or associated with any session, it’s in transient state. Transient instances may be made persistent by calling save(), persist() or saveOrUpdate(). Persistent instances may be made transient by calling delete().
-	**Persistent**: When an object is associated with a unique session, it’s in persistent state. Any instance returned by a get() or load() method is persistent.
-	**Detached**: When an object is previously persistent but not associated with any session, it’s in detached state. Detached instances may be made persistent by calling update(), saveOrUpdate(), lock() or replicate(). The state of a transient or detached instance may also be made persistent as a new persistent instance by calling merge().

As you know that **Hibernate** works with normal Java objects that your application creates with the new operator. In raw form (without annotations), hibernate will not be able to identify your java classes; but when they are properly annotated with required annotations then hibernate will be able to identify them and then work with them e.g. store in DB, update them etc. These objects can be said to mapped with hibernate.

Given an instance of an object that is mapped to Hibernate, it can be in any one of four different states: **transient, persistent, detached, or removed.** 

![]({{site.cdn}}/hibernate/entity-lifecycle.png)

