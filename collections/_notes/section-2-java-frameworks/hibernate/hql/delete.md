---
layout: post
title: HQL Delete
permalink: /:collection/hibernate/hql/delete
---

DELETE removes the details of existing objects from the database. In-memory entities will not be updated to reflect changes resulting from DELETE statements. This also means that Hibernate’s cascade rules will not be followed for deletions carried out using HQL. However, if you have specified cascading deletes at the database level (either directly or through Hibernate, using the @OnDelete annotation), the database will still remove the child rows.

```sql
DELETE
   [FROM] path [[AS] alias]
   [WHERE logicalExpression]
```
```java
Query query=session.createQuery("delete from Account where accountstatus=:status");
query.setString("status", "purged");
int rowsDeleted=query.executeUpdate();
```

