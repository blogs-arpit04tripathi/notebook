---
layout: post
title: SQL Injection
permalink: /:collection/hibernate/queries/sql-injection
---

```java
String minUserId = "5";		// User input as string
quryString = "from User Details where userId > "+ minUserId;
```
Here, user can enter minUserId = "5 or 1=1";  
This is called SQLInjection. To avoid it, we can use parameter binding.
```java
Query q = session.createQuery("from UserDetails where userId > ? and username = ?");
q.setInteger(0, Integer.parseInt(minUserId));
q.setString(1, username);

Query q = session.createQuery("from UserDetails where userId > :userId and username = :username");
q.setInteger("userId", Integer.parseInt(minUserId));
q.setString("username", name);
```
