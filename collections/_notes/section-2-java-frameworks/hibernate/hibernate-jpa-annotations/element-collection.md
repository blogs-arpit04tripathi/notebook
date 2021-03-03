---
layout: post
title: Annotation @ElementCollection
permalink: /:collection/hibernate/annotations/element-collection
---

@ElementCollection annotation for mapping collections of basic or embeddable classes.
```java
@ElementCollection
List<String> passwordHints;
```
two attributes on the @ElementCollection annotation: **targetClass** and **fetch**. The targetClass attribute tells Hibernate which class is stored in the collection. If you use generics on your collection, you do not need to specify targetClass because Hibernate will infer the correct class. The fetch attribute takes a member of the enumeration, FetchType. This is EAGER by default, but can be set to LAZY to permit loading when the value is accessed.

![]({{site.cdn}}/hibernate/element-collection.png)

```java
@ElementCollection
@JoinTable(name="USER_ADDRESS", joinColumns={@JoinColumn(name="USER_ID")})
@GenericGenerator(name="hilo-gen", strategy="hilo")
@CollectionId(columns={@Column(name="ADDRESS_ID")}, generator="hilo-gen", type=@Type(type="long"))
private Collection<Address> addresses = new ArrayList<>();
```
Here USER_ADDRESS has a Foreign Key but no Primary Key hence we use @CollectionId of hibernate specific annotation. To have an indexed order, we have to select a datatype that supports index, ex. ArrayList.

