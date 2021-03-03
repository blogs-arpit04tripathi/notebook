---
layout: post
title: Removed Object
permalink: /:collection/hibernate/persistence/removed
---

Removed objects are objects that are being managed by Hibernate (persistent objects, in other words) that have been passed to the session’s remove() method. When the application marks the changes held in the session as to be committed, the entries in the database that correspond to removed objects are deleted.

**Bullet Points**
1.	Newly created POJO object will be in the transient state. Transient object doesn’t represent any row of the database i.e. not associated with any session object. It’s plain simple java object.
2.	Persistent object represent one row of the database and always associated with some unique hibernate session. Changes to persistent objects are tracked by hibernate and are saved into database when commit call happen.
3.	Detached objects are those who were once persistent in past, and now they are no longer persistent. To persist changes done in detached objects, you must reattach them to hibernate session.
4.	Removed objects are persistent objects that have been passed to the session’s remove() method and soon will be deleted as soon as changes held in the session will be committed to database.

```java
UserDetails user = new UserDetails(); //Transient Object
User.setUserName("Arpit Tripathi");
SessionFactory sf = new Configuration().configure().buildSessionFactory();
Session s = sf.openSession();
s.beginTransaction();
s.save(user);	//Persistent
user.setUserName("Update Arpit Tripathi");
s.getTransaction().commit();
s.close;
```

-	Until we pass the object to hibernate, it is a transient object. On calling session.save, the object is handed to hibernate and becomes persistent.
-	After session.save(), whatever changes you make will go as update statement. Last state ie. State of object at the time of commit will be reflected in DB.
-	Hibernate will watch for changes in persistent objects
-	After session.close(), object becomes detached.

```
Transient – Hibernate doesn’t know about it.
Persistent – Hibernate is tracking it.
Detached – Had been tracked by hibernate.
```

