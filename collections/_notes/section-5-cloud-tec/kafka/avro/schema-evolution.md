---
layout: post
title: Schema Evolution (Avro Schemas)
permalink: /:collection/kafka/schema-evolution
---

![]({{site.cdn}}/kafka/schema-evolution.png)

![]({{site.cdn}}/kafka/avro-overview.png)

![]({{site.cdn}}/kafka/avro-serialization.png)

```java
props.put("value.deserializer", "io.consfluent.kafka.serializers.KafkaAvroDeserializer");
props.put("schema.registry.url", "http://localhost:8081");
props.put("specific.avro.reader", "true");
```

-	Confluent Platform Quickstart
-	Confluent Platform – rpm packages by yum
-	Schema resolution

![]({{site.cdn}}/kafka/confluent-platform.png)
