---
layout: post
title: POST vs PUT vs PATCH
permalink: /:collection/spring/rest/post-vs-put-vs-patch
---


- **Safe Methods** - method never modifies nor changes a resource.
- **Idempotent** - operation performed N number of times, end result is always same.
- HttpMethods
  - GET - Idempotent and Safe
  - POST - none
  - PUT - Idempotent
  - PATCH - Idempotent
  - OPTIONS - Idempotent and Safe
  - HEAD - Idempotent and Safe
  - DELETE - Idempotent

# POST
-	allows us to create a resource.
-	Always create a new house at a different location
  - will always generate a different (unique) system ID.

```
http://domain.com/house

{
  "front_garden": true,
  "back_garden": true,
  "windows": 3,
  "doors": 2,
  "garage": true
}
```

# PUT
-	Replaces complete body for id.
  -	PUT for non-existing, creates new record.

```
http://domain.com/house/1

{
  "front_garden": true,
  "back_garden": true,
  "windows": 13,
  "doors": 3,
  "garage": false
}
```
House with only windows
```
{"windows": 8}
```

# PATCH
- partial update

```
{"windows": 8}
```
```
{
  "front_garden": true,
  "back_garden": true,
  "windows": 8,
  "doors": 3,
  "garage": false
}
```
