---
layout: post
title: HQL – from clause and aliases
permalink: /:collection/hibernate/hql/from
---

```sql
from Product as p 
or
from Product product
```

The from clause is very basic and useful for working directly with objects. However, if you want to work with the object’s properties without loading the full objects into memory, you must use the select clause as explained in next section.

