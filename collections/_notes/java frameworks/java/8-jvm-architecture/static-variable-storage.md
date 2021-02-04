---
layout: post
title: Where static variables are stored from Java 8
permalink: /java/static-variable-storage
---

- **Java 7**
  - static variables were stored in the permgen space.
  - PermGen Space is also known as Method Area
  - PermGen Space used to store 3 things
    - Class level data (meta-data)
    - interned strings(String Pool)
    - static variables
- **From Java 8 onwards**
  - ***static variables are stored in the Heap itself.***
  - PermGen Space is removed and new space, **MetaSpace** is introduced which is not the part of Heap any more.
  - MetaSpace is present on the native memory
    - memory provided by the OS to a particular Application for its own usage
  - MetaSpace - class meta-data and string pool

![jmm-java8](https://github.com/arpit04tripathi/files-cdn/raw/cdn/java/jvm-architecture/jmm-java8.png)

