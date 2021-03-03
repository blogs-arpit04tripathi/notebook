---
layout: post
title: Elasticache vs Redshift
permalink: /:collection/aws/elasticache/elasticache-vs-redshift
---

* Scenario : Particular DB is under a lot of stress/load, which service will you alleviate.
    - Elasticache, if your DB is particularly read-heavy and not prone to frequent changing.
    - Redshift, if your DB is feeking stress because management keep running OLAP transactions on it.

