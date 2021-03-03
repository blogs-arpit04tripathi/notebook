---
layout: post
title: HQL Update
permalink: /:collection/hibernate/hql/update
---

```sql
UPDATE [VERSIONED]
   [FROM] path [[AS] alias] [, ...]
   SET property = value [, ...]
   [WHERE logicalExpression]
```
```java
Query query=session.createQuery("update Employee set age=:age where name=:name");
query.setInteger("age", 32);
query.setString("name", "Lokesh Gupta");
int modifications=query.executeUpdate();
```
-	**path** – fully qualified name of the entity or entities
-	**alias** – used to abbreviate references to specific entities or their properties, and must be used when property names in the query would otherwise be ambiguous.
-	**VERSIONED** – means that the update will update time stamps, if any, that are part of the entity being updated.
-	**property** – names of properties of entities listed in the FROM path.
-	**logicalExpression** – a where clause.

