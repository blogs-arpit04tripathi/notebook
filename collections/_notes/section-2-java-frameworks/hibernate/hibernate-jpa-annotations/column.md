---
layout: post
title: Annotation @Column
permalink: /:collection/hibernate/annotations/column
---

used to specify the details of the column to which a field or property will be mapped. 

attributes commonly being overridden:
1.	**name** : permits the name of the column to be explicitly specified—by default, this would be the name of the property.
2.	**length** : permits the size of the column used to map a value (particularly a String value) to be explicitly defined. The column size defaults to 255, which might otherwise result in truncated String data, for example.
3.	**nullable** : permits the column to be marked NOT NULL when the schema is generated. The default is that fields should be permitted to be null; however, it is common to override this when a field is, or ought to be, mandatory.
4.	**unique** : permits the column to be marked as containing only unique values. This defaults to false, but commonly would be set for a value that might not be a primary key but would still cause problems if duplicated (such as username).

```java
@Column(name="FNAME",length=100,nullable=false)
private String  firstName;
```
```java
@Temporal(TemporalType.TIME)
java.util.Date startingTime;
```
