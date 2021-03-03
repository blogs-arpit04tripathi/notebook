---
layout: post
title: Hibernate lazy loading – why we need it?
permalink: /:collection/hibernate/lazy-loading/why
---

-	Consider one of common Internet web application: the online store. The store maintains a catalog of products. At the crudest level, this can be modeled as a catalog entity managing a series of product entities. In a large store, there may be tens of thousands of products grouped into various overlapping categories.
-	When a customer visits the store, the catalog must be loaded from the database. We probably don’t want the implementation to load every single one of the entities representing the tens of thousands of products to be loaded into memory. For a sufficiently large retailer, this might not even be possible, given the amount of physical memory available on the machine.
-	Even if this was possible, it would probably cripple the performance of the site. Instead, we want only the catalog to load, possibly with the categories as well. Only when the user drills down into the categories should a subset of the products in that category be loaded from the database.
-	To manage this problem, Hibernate provides a facility called **lazy loading**. When enabled, an entity’s associated entities will be loaded only when they are directly requested.

