---
layout: post
title: Annotation @Id, @IdClass, or @EmbeddedId (Compound Primary Keys)
permalink: /:collection/hibernate/annotations/embedded-id
---

For multi-column primary key, You must create a class to represent this primary key. It will not require a primary key of its own, of course, but it must be a public class, must have a default constructor, must be serializable, and must implement hashCode() and equals() methods to allow the Hibernate code to test for primary key collisions.

Your three strategies for using this primary key class once it has been created are as follows:
1.	Mark it as @Embeddable and add to your entity class a normal property for it, marked with @Id.
2.	Add to your entity class a normal property for it, marked with @EmbeddableId.
3.	Add properties to your entity class for all of its fields, mark them with @Id, and mark your entity class with @IdClass, supplying the class of your primary key class.

The use of @Id with a class marked as @Embeddable is the most natural approach. The @Embeddable tag can be used for non-primary key embeddable values anyway. It allows you to treat the compound primary key as a single property, and it permits the reuse of the @Embeddable class in other tables.

One thing worth pointing out: the embedded primary key classes must be serializable.

```java
// Example 1:
@Embeddable 
public class EmploymentPeriod { 
       @Temporal(DATE) 
       java.util.Date startDate;
       @Temporal(DATE) 
       java.util.Date endDate;
      ... 
    }

Example 2:
// @Embeddable – Tells hibernate not to create a table for the class.
@Embeddable 
public class PhoneNumber {
        protected String areaCode;
        protected String localNumber;
        @ManyToOne PhoneServiceProvider provider;
        ...
     }

@Entity 
public class PhoneServiceProvider {
        @Id protected String name;
         ...
     }

// Example 3:
@Embeddable 
public class Address {
       protected String street;
       protected String city;
       protected String state;
       @Embedded
       protected Zipcode zipcode;
    }

@Embeddable 
public class Zipcode {
       protected String zip;
       protected String plusFour;
     }
```

![]({{site.cdn}}/hibernate/embeddable.png)

In this case @Embeddable and @Embedded will work. But what if we have Home Address and Office Address? @Embedded will be there but field names will conflict, hence override its attribute.

```java
@Embedded
@AttributeOverrides({
   @AttributeOverride(name="street",   
        column=@Column(name="Office_Street")), 
   @AttributeOverride(name="city",   
        column=@Column(name="Office_City"))
})
private Address homeAddress;
```

-	**Entity** – Data + Needs to be saved independently ie. Has a meaning of its own
-	**Value Object** – Data + Needs to be saved, but doesn’t have a meaning of itself(dependent). Example – Address (who’s address)
