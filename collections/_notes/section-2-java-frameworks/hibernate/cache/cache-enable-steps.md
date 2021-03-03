---
layout: post
title: Steps For Enabling Cachce
permalink: /:collection/hibernate/cache/enable-steps
---

**Step 1.**	Add hibernate-ehcache dependency in your maven project, if it’s not maven then add corresponding jars.

```xml
<!-- EHCache Core APIs --> 
<dependency> 
	<groupId>net.sf.ehcache</groupId> 
	<artifactId>ehcache-core</artifactId> 
	<version>2.6.9</version> 
</dependency> 
<!-- Hibernate EHCache API --> 
<dependency> 
	<groupId>org.hibernate</groupId> 
	<artifactId>hibernate-ehcache</artifactId> 
	<version>4.3.5.Final</version> 
</dependency> 
<!-- EHCache uses slf4j for logging --> 
<dependency> 
	<groupId>org.slf4j</groupId> 
	<artifactId>slf4j-simple</artifactId> 
	<version>1.7.5</version> 
</dependency>
```

**Step 2.**	Add below properties in hibernate configuration file.

```xml
<property name="hibernate.cache.region.factory_class">org.hibernate.cache.ehcache.EhCacheRegionFactory</property>
         
<!-- For singleton factory -->
<property name="hibernate.cache.region.factory_class">org.hibernate.cache.ehcache.SingletonEhCacheRegionFactory</property>
          
<!-- enable second level cache and query cache -->
<property name="hibernate.cache.use_second_level_cache">true</property>
<property name="hibernate.cache.use_query_cache">true</property>
<property name="net.sf.ehcache.configurationResourceName">/myehcache.xml</property>
```

**Step 3.**	Create EHCache configuration file, a sample file myehcache.xml would look like below.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<ehcache xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:noNamespaceSchemaLocation="ehcache.xsd" updateCheck="true"
    monitoring="autodetect" dynamicConfig="true">
 
    <diskStore path="java.io.tmpdir/ehcache" />
 
    <defaultCache maxEntriesLocalHeap="10000" eternal="false"
        timeToIdleSeconds="120" timeToLiveSeconds="120" diskSpoolBufferSizeMB="30"
        maxEntriesLocalDisk="10000000" diskExpiryThreadIntervalSeconds="120"
        memoryStoreEvictionPolicy="LRU" statistics="true">
        <persistence strategy="localTempSwap" />
    </defaultCache>
 
    <cache name="employee" maxEntriesLocalHeap="10000" eternal="false"
        timeToIdleSeconds="5" timeToLiveSeconds="10">
        <persistence strategy="localTempSwap" />
    </cache>
 
    <cache name="org.hibernate.cache.internal.StandardQueryCache"
        maxEntriesLocalHeap="5" eternal="false" timeToLiveSeconds="120">
        <persistence strategy="localTempSwap" />
    </cache>
 
    <cache name="org.hibernate.cache.spi.UpdateTimestampsCache"
        maxEntriesLocalHeap="5000" eternal="true">
        <persistence strategy="localTempSwap" />
    </cache>
</ehcache>
```

-	**diskStore**: EHCache stores data into memory but when it starts overflowing, it start writing data into file system. We use this property to define the location where EHCache will write the overflown data.
-	**defaultCache**: It’s a mandatory configuration, it is used when an Object need to be cached and there are no caching regions defined for that.
-	**cache name="employee"**: We use cache element to define the region and it’s configurations. We can define multiple regions and their properties, while defining model beans cache properties, we can also define region with caching strategies. The cache properties are easy to understand and clear with the name.
-	Cache regions **org.hibernate.cache.internal.StandardQueryCache** and **org.hibernate.cache.spi.UpdateTimestampsCache** are defined because EHCache was giving warning to that.

**Step 4.**	Annotate entity beans with @Cache annotation and caching strategy to use. For example,

```java
import org.hibernate.annotations.Cache;
import org.hibernate.annotations.CacheConcurrencyStrategy;

@Entity
@Table(name = "ADDRESS")
@Cache(usage=CacheConcurrencyStrategy.READ_ONLY, region="employee")
public class Address {

}
```
That’s it, we are done. Hibernate will use the EHCache for second level caching, read Hibernate EHCache Example for a complete example with explanation.

```java
Session session = SessionFactory.openSession();
Query query = session.createQuery("FROM EMPLOYEE");
query.setCacheable(true);
List users = query.list();
SessionFactory.closeSession();

Session session = SessionFactory.openSession();
Query query = session.createQuery("FROM EMPLOYEE");
query.setCacheable(true);
query.setCacheRegion("employee");
List users = query.list();
SessionFactory.closeSession();
```
