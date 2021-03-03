---
layout: post
title: Detached to Persistent
permalink: /:collection/hibernate/persistence/detached-to-persistent
---

- User may take time hence we have to create a session to fetch and then close it. Here, the object become detached.
- Now user may upfate the a member variable that needs to be saved. To save it, open a new session and call the session.update(user).

```java
session2 = sessionFactory.openSession();
session2.beginTransaction();
session2.update(user);
// Update runs even though nothing changed as session1 was closed making it detached.
// user.setUserName("Updated Users");
session2.getTransaction().commit();
session2.close();   // Now user is a transient object.
```

![]({{site.cdn}}/hibernate/detached-to-persistent.png)

To stop this extra update query from running, we would instruct hibernate to run a select query and check if any changes are made. Update only if there are changes.
```java
@Entity
@org.hibernate.annotations.Entity(selectBeforeUpdate=true)
```
Now, only select query is run for no change scenario.
```java
User.senName("Test");
Session.update(user);	// Select + Update Query
```
