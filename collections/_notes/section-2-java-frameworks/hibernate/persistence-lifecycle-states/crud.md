---
layout: post
title: CRUD (Create / Read / Update / Delete)
permalink: /:collection/hibernate/persistence/crud
---

```java
session.save(user);
session.get(UserDetails.class, id);
session.delete(user);
user.setName("Updated");
session.update(user);
```

![]({{site.cdn}}/hibernate/persistence-crud.png)

