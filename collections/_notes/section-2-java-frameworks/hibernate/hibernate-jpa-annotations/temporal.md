---
layout: post
title: Annotation @Temporal
permalink: /:collection/hibernate/annotations/temporal
---

java.util.Date or java.util.Calendar types represent temporal data. By default, these will be stored in a column with the **TIMESTAMP** data type, but this default behavior can be overridden with the @Temporalannotation.

TemporalType enum - **DATE**, **TIME**, and **TIMESTAMP**
