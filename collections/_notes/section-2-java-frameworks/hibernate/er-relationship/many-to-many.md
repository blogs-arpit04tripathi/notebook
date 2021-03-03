---
layout: post
title: Many to Many
permalink: /:collection/hibernate/mapping/many-to-many
---

**Hibernate many to many mapping** is made between two entities where one can have relation with multiple other entity instances. For example, for a subscription service SubscriptionEntity and ReaderEntity can be two type of entities. Any subscription can have multiple readers, where a reader can subscribe to multiple subscriptions.

![]({{site.cdn}}/hibernate/ManytoMany.png)

Owner entity is the entity which is **responsible make making the association and maintaining it.** In our case, I am making ReaderEntity the owner entity. **@JoinTable** annotation has been used to make this association.

```java
@Entity(name = "ReaderEntity")
@Table(name = "READER", uniqueConstraints = {
    @UniqueConstraint(columnNames = "ID"),
    @UniqueConstraint(columnNames = "EMAIL")
})

public class ReaderEntity implements Serializable {
    private static final long serialVersionUID = -1798070786993154676 L;

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    @Column(name = "ID", unique = true, nullable = false)
    private Integer readerId;

    @ManyToMany(cascade = CascadeType.ALL)
    @JoinTable(name = "READER_SUBSCRIPTIONS",
        joinColumns = {
            @JoinColumn(referencedColumnName = "ID")
        }, inverseJoinColumns = {
            @JoinColumn(referencedColumnName = "ID")
        })
    private Set < SubscriptionEntity > subscriptions;
}
```
```java
@Entity(name = "SubscriptionEntity")
@Table(name = "SUBSCRIPTION", uniqueConstraints = {
    @UniqueConstraint(columnNames = "ID")
})
public class SubscriptionEntity implements Serializable {
    private static final long serialVersionUID = -6790693372846798580 L;

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    @Column(name = "ID", unique = true, nullable = false)
    private Integer subscriptionId;

    @ManyToMany(mappedBy = "subscriptions")
    private Set < ReaderEntity > readers;
}
```

