---
layout: post
title: How to enable lazy loading in hibernate
permalink: /:collection/hibernate/lazy-loading/how-to-enable
---

Before moving further, it is important to recap the default behavior of lazy loading in case of using hibernate mappings vs annotations.

-	The default behavior is to load ‘property values eagerly’ and to load ‘collections lazily’. Contrary to what you might remember if you have used plain Hibernate 2 (mapping files) before, where all references (including collections) are loaded eagerly by default.
-	Also note that @OneToMany and @ManyToMany associations are defaulted to LAZY loading; and @OneToOne and @ManyToOne are defaulted to EAGER loading. This is important to remember to avoid any pitfall in future.

To enable lazy loading explicitly you must use **"fetch = FetchType.LAZY"** on a association which you want to lazy load when you are using hibernate annotations.

A **hibernare lazy load example** will look like this:
```java
@OneToMany( mappedBy = "category", fetch = FetchType.LAZY )
private Set<ProductEntity> products;
```
Another attribute parallel to "FetchType.LAZY" is "FetchType.EAGER" which is just opposite to LAZY i.e. it will load association entity as well when owner entity is fetched first time.

