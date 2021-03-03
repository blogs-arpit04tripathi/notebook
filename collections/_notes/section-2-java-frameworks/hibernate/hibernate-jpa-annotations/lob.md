---
layout: post
title: Annotation @Lob
permalink: /:collection/hibernate/annotations/lob
---

String- and character-based types will be stored in an appropriate character-based type i.e. CLOB. All other objects will be stored in a BLOB.

```java
@Lob
String content; // a very long article
```

@Lob annotation can be used in combination with the @Basic or the @ElementCollection annotation.
