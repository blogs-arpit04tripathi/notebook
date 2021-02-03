---
layout: post
title: CopyOnWriteArrayList
permalink: /java/collections/copyOnWriteArrayList
---

* Thread safe variant of ArrayList.
* mutative operations like add, set are implemented by creating a fresh copy of the underlying array.
* Doesn’t throw **currentModificationException**.
* Allows null.
