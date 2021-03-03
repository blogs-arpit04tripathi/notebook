---
layout: post
title: Hibernate Transaction Management
permalink: /:collection/hibernate/transaction-management
---

**How transaction management works in Hibernate?**  
-	Transaction management is very easy in hibernate because most of the operations are not permitted outside of a transaction. So after getting the session from SessionFactory, we can call session beginTransaction() to start the transaction.
-	This method returns the Transaction reference that we can use later on to either commit or rollback the transaction.
-	Overall hibernate transaction management is better than JDBC transaction management because we don’t need to rely on exceptions for rollback. Any exception thrown by session methods automatically rollback the transaction.

**What is HibernateTemplate class?**  
-	When Spring and Hibernate integration started, Spring ORM provided two helper classes – `HibernateDaoSupport` and `HibernateTemplate`. The reason to use them was to get the Session from Hibernate and get the benefit of Spring transaction management. However from Hibernate 3.0.1, we can use `SessionFactory` *getCurrentSession()* method to get the current session and use it to get the spring transaction management benefits. If you go through above examples, you will see how easy it is and that’s why we should not use these classes anymore.
-	One other benefit of `HibernateTemplate` was exception translation but that can be achieved easily by using `@Repository` annotation with service classes, shown in above spring mvc example. This is a trick question to judge your knowledge and whether you are aware of recent developments or not.
