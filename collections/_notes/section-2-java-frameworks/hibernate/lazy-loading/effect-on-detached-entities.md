---
layout: post
title: Effect of lazy loading on detached entities
permalink: /:collection/hibernate/lazy-loading/effect-on-detached-entities
---

-	As we know that hibernate can only access the database via a session, So If an entity is detached from the session and when we try to access an association (via a proxy or collection wrapper) that has not yet been loaded, **Hibernate throws a LazyInitializationException.**
-	The cure is to ensure either that the entity is made persistent again by attaching it to a session or that all of the fields that will be required are accessed (so they are loaded into entity) before the entity is detached from the session.

![]({{site.cdn}}/hibernate/lazy-loading.png)

|Default Fetch Type||
|---|---|
|@OneToOne|FetchType.EAGER|
|@OneToMany|FetchType.LAZY|
|@ManyToOne|FetchType.EAGER|
|@ManyToMany|FetchType.LAZY|

```java
User user = (User) session.get(User.class, id);   //List of address not pulled here user.getListOfAddress();
```
Here query runs to actually fetch from DB.

Lazy initialization: Fetch first level member variables to initialize the proxy.  
**Proxy Class**: Dynamic Subclass of your objects’ class

- Hibernate creates Proxy Class, and to initialize fills in 1st level member variables and returns proxy object.  
- getId() internally calls parent.getID() hence difference not noticed by end user.

```java
user = (User) session.get(User.class, id);
session.close();
user.getListOfAddress();
// LazyInitializationException is thrown
```
```java
@ElementCollection(fetch="FetchType.EAGER")
```
Still in this case, a proxy object is returned as there might be another collection with LAZY fetchType.

