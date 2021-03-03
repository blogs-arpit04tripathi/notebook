---
layout: post
title: Offsets
permalink: /:collection/kafka/consumer/offsets
---

- **Current Offset**
  - Current offset for the consumer.
- **committed offset**
  - consumer confirms to consumer group that the records are read successfully for the partition till this offset.
  - Important in case of repartition, new consumer will start after committed offset.
