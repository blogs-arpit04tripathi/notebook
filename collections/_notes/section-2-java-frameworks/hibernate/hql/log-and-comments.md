---
layout: post
title: HQL – Enable Logs and Comments
permalink: /:collection/hibernate/hql/log-and-comments
---

# HQL Logs
The easiest way to see the SQL for a Hibernate HQL query is to enable SQL output in the logs with the **"show_sql"** property.
When you look in your application’s output for the Hibernate SQL statements, they will be prefixed with "Hibernate:".
If you turn your log4j logging up to debug for the Hibernate classes, you will see SQL statements in your log files, along with lots of information about how Hibernate parsed your HQL query and translated it into SQL.

# HQL Comments
Tracing your HQL statements through to the generated SQL can be difficult, so Hibernate provides a commenting facility on the Query object that lets you apply a comment to a specific query.
```java
public Query setComment(String comment)
```
-	Hibernate will not add comments to your SQL statements without some additional configuration, even if you use the setComment()method. You will also need to set a Hibernate property, **hibernate.use_sql_comments**, to true in your Hibernate configuration. 
-	If you set this property but do not set a comment on the query programatically, Hibernate will include the HQL used to generate the SQL call in the comment. I find this to be very useful for debugging HQL.
-	Use commenting to identify the SQL output in your application’s logs if SQL logging is enabled.
