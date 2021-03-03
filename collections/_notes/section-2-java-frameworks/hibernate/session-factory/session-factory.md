---
layout: post
title: SessionFactory and Session
permalink: /:collection/hibernate/session-factory
---

**SessionFactory**
- Reads hibernate config file
- Creates Session Objects
- Heavy weight object, created only once in your application.

**Session**
- Wraps a JDBC connection
- Main object used to save/retrieve object
- Short lived object
- Retrieved from session factory

**What is Hibernate SessionFactory and how to configure it?**  
-	Factory class responsible to read the hibernate config params and connect to the DB and provide Session objects. 
-	Usually an application has a single SessionFactory instance and threads servicing client requests obtain Session instances from this factory.
-	The internal state of a SessionFactory is immutable. Once it is created this internal state is set. This internal state includes all of the metadata about Object/Relational Mapping.
-	SessionFactory also provide methods to get the Class metadata and Statistics instance to get the stats of query executions, second level cache details etc.

**Classes used in building SessionFactory**  
I have used following classes for building SessionFactory in hibernate 4.
1.	**Configuration** : In place of deprecated AnnotationConfiguration
2.	**StandardServiceRegistryBuilder** : In place of deprecated ServiceRegistryBuilder

```java
public class HibernateUtil{
   private static SessionFactory sessionFactory = buildSessionFactory();
   private static SessionFactory buildSessionFactory()  {
      try {
         if (sessionFactory == null)  {
            Configuration configuration = new Configuration().configure(HibernateUtil.class.getResource("/hibernate.cfg.xml"));
            StandardServiceRegistryBuilder serviceRegistryBuilder = new StandardServiceRegistryBuilder();
            serviceRegistryBuilder.applySettings(configuration.getProperties());
            ServiceRegistry serviceRegistry = serviceRegistryBuilder.build();
            sessionFactory = configuration.buildSessionFactory(serviceRegistry);
         }
         return sessionFactory;
      } catch (Throwable ex) {
         System.err.println("Initial SessionFactory creation failed." + ex);
         throw new ExceptionInInitializerError(ex);
      }
   }
   public static SessionFactory getSessionFactory()  {      return sessionFactory;   }
   public static void shutdown()   {      getSessionFactory().close();   }
}
```

**Hibernate SessionFactory is thread safe?**  
Internal state of SessionFactory is immutable, so it’s thread safe. Multiple threads can access it simultaneously to get Session instances.

**What is Hibernate Session and how to get it?**  
-	Hibernate Session is the interface between java application layer and hibernate. 
-	core interface used to perform DB operations. 
-	Lifecycle of a session is bound by the beginning and end of a transaction.
-	Session provide methods to perform create, read, update and delete operations for a persistent object. 
-	We can execute HQL queries, SQL native queries and create criteria using Session object.

**Hibernate Session is thread safe?**  
Hibernate Session object is not thread safe, every thread should get its own session instance and close it after its work is finished.

**What is difference between openSession and getCurrentSession?**  
**getCurrentSession()** - returns the session bound to the context. But for this to work, we need to configure it in hibernate configuration file. Since this session object belongs to the hibernate context, we don’t need to close it. Once the session factory is closed, this session object gets closed.  
Hibernate Session objects are not thread safe, so we should not use it in multi-threaded environment. We can use it in single threaded environment because it’s relatively faster than opening a new session.

```xml
<property name="hibernate.current_session_context_class">thread</property>
```

**openSession()**   
-	Always opens a new session. We should close this session object once we are done with all the database operations. We should open a new session for each request in multi-threaded environment.
-	For web application frameworks, we can choose to open a new session for each request or for each session based on the requirement.

**openStatelessSession()**   
-	returns instance of StatelessSession. 
-	StatelessSession in Hibernate does not implement first-level cache and it doesn’t interact with any second-level cache. Since it’s stateless, it doesn’t implement transactional write-behind or automatic dirty checking or do cascading operations to associated entities.
-	Collections are also ignored by a stateless session. Operations performed via a stateless session bypass Hibernate’s event model and interceptors. It’s more like a normal JDBC connection and doesn’t provide any benefits that come from using hibernate framework.
-	However, stateless session can be a good fit in certain situations. For example where we are loading bulk data into database and we don’t want hibernate session to hold huge data in first-level cache memory.

```java
public class HibernateUtil {
    private static final SessionFactory sessionFactory = buildSessionFactory();
    private static SessionFactory buildSessionFactory() {
        try {
            // Create the SessionFactory from hibernate.cfg.xml
            return new AnnotationConfiguration().configure(new File("hibernate.cgf.xml")).buildSessionFactory();
        } catch (Throwable ex) {
            // Make sure you log the exception, as it might be swallowed
            System.err.println("Initial SessionFactory creation failed." + ex);
            throw new ExceptionInInitializerError(ex);
        }
    }

    public static SessionFactory getSessionFactory() {
        return sessionFactory;
    }

    public static void shutdown() {
        // Close caches and connection pools
        getSessionFactory().close();
    }
}
```
```java
//Current Session - no need to close Session 
currentSession = sessionFactory.getCurrentSession(); 
//open new session 
Session newSession = sessionFactory.openSession(); 
//perform db operations and close session 
newSession.close(); 
//open stateless session 
StatelessSession statelessSession = sessionFactory.openStatelessSession(); 
//perform stateless db operations and close session 
statelessSession.close(); 
//close session factory 
sessionFactory.close();
```

**What is difference between Hibernate Session get() and load() method?**  

|get()|	load()|
|---|---|	
|loads the data as soon as it’s called|	returns a proxy object and loads data only when actually required|
|Eager loading|	support lazy loading.|
|Returns null|	throws ObjectNotFoundException when data is not found|
|use get() when we want to make sure data exists in the DB.|	should use it only when we know data exists.|

**What is difference between Hibernate save(), saveOrUpdate() and persist() methods?**  
-	**save()** - can be used to save entity to database. Problem with save() is that it can be invoked without a transaction and if we have mapping entities, then only the primary object gets saved causing data inconsistencies. Also save returns the generated id immediately.
-	**persist()** - similar to save with transaction. I feel it’s better than save because we can’t use it outside the boundary of transaction, so all the object mappings are preserved. Also persist doesn’t return the generated id immediately, so data persistence happens when needed.
-	**saveOrUpdate()** - results into insert or update queries based on the provided data. If the data is present in the database, update query is executed. We can use saveOrUpdate() without transaction also, but again you will face the issues with mapped objects not getting saved if session is not flushed. 

> For example usage of these methods, read [Hibernate save vs persist]( http://www.journaldev.com/3481/hibernate-session-merge-vs-update-save-saveorupdate-persist-example){:target="_blank"}

**Suggestion For production code – best practices**  
It wouldn’t be advisable to try to use above code in production code. Ideally, what you would do is pass VO object to DAO layer, load the entity from the session and update the entity with by copying VO data onto it. This means that the updates take place on a persistent object, and we don’t actually have to call Session.save() or Session.saveOrUpdate() at all.

Once an object is in a persistent state, Hibernate manages updates to the database itself as you change the fields and properties of the object. It’s big relief.

**Summary**
-	Save() method stores an object into the database. It will Persist the given transient instance, first assigning a generated identifier. It returns the id of the entity created.
-	SaveOrUpdate() calls either save() or update() on the basis of identifier exists or not. e.g if identifier does not exist, save() will be called or else update() will be called.
-	Probably you will get very few chances to actually call save() or saveOrUpdate() methods, as hibernate manages all changes done in persistent objects.

**What is use of Hibernate Session merge() call?**  
Hibernate merge can be used to update existing values, however this method creates a copy from the passed entity object and return it. The returned object is part of persistent context and tracked for any changes, passed object is not tracked. 

> For example program, read [Hibernate merge](http://www.journaldev.com/3481/hibernate-session-merge-vs-update-save-saveorupdate-persist-example){:target="_blank"}

**refresh()**  
Sometimes we face situation where we application database is modified with some external application/agent and thus corresponding hibernate entity in your application actually becomes out of sync with it’s database representation i.e. having old data. In this case, you can use **session.refresh() method to re-populate the entity with latest data available in database**.

-	Method merge() does exactly opposite to what refresh() does i.e. It updates the database with values from a detached entity. Refresh method was updating the entity with latest database information. So basically, both are exactly opposite.
-	Merging is performed when you desire to have a **detached entity changed to persistent state** again, with the detached entity’s changes migrated to (or overriding) the database.
-	Copy the state of the given object onto the persistent object with the same identifier. If there is no persistent instance currently associated with the session, it will be loaded. Return the persistent instance. If the given instance is unsaved, save a copy of and return it as a newly persistent instance. The given instance does not become associated with the session. This operation cascades to associated instances if the association is mapped with cascade="merge".

**What will happen if we don’t have no-args constructor in Entity bean?**  
Hibernate uses Reflection API to create instance of Entity beans, usually when you call get() or load() methods. The method Class.newInstance() is used for this and it requires no-args constructor. So if you won’t have no-args constructor in entity beans, hibernate will fail to instantiate it and you will get HibernateException.

