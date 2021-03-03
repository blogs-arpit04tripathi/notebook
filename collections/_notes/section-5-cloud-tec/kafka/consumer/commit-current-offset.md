---
layout: post
title: Commit Current Offset
permalink: /:collection/kafka/consumer/commit-current-offset
---

- **AUTO COMMIT**
  - enable.auto.commit – Default true
  - Auto.commit.interval.ms – Default 5 sec.
  - Chances of double-reading are there.
- **MANUAL COMMIT**
  - consumer.commitSync() - blocking
  - consumer.commitAsync() – non blocking and no retry.

![]({{site.cdn}}/kafka/commit-current-offset.png)
