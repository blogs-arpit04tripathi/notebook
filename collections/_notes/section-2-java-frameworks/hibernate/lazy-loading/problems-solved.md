---
layout: post
title: How lazy loading solve above problem
permalink: /:collection/hibernate/lazy-loading/problems-solved
---

Now when we have understood the problem, let’s understand how lazy loading actually helps in real life. If we consider to solve the problem discussed above then we would be accessing a category (or catalog) in below manner:

```java
//Following code loads only a single category from the database:
Category category = (Category)session.get(Category.class,new Integer(42));
```
However, **if all products of this category are accessed, and lazy loading is in effect, the products are pulled from the database as needed.** For instance, in the following snippet, the associated product objects will be loaded since it is explicitly referenced in second line.

```java
//Following code loads only a single category from the database
Category category = (Category)session.get(Category.class,new Integer(42));
//This code will fetch all products for category 42 from database - "NOW"
Set<Product> products = category.getProducts();
```
This solve our problem of loading the products only when they are needed.

