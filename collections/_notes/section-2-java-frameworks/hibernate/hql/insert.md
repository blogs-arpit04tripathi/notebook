---
layout: post
title: HQL Insert
permalink: /:collection/hibernate/hql/insert
---

An HQL INSERT **cannot be used to directly insert arbitrary entities**—it can only be used to insert entities constructed from information obtained from SELECT queries (unlike ordinary SQL, in which an INSERT command can be used to insert arbitrary data into a table, as well as insert values selected from other tables).

```sql
INSERT INTO path ( property [, ...]) select 
```

```java
Query query=session.createQuery("insert into purged_accounts(id, code, status) "+
    "select id, code, status from account where status=:status");
query.setString("status", "purged");
int rowsCopied=query.executeUpdate();
```
