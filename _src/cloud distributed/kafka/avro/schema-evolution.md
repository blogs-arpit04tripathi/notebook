---
layout: post
title: Schema Evolution (Avro Schemas)
permalink: /kafka/schema-evolution
---

![](https://github.com/arpit04tripathi/files-cdn/raw/cdn/kafka/schema-evolution.png)

![](https://github.com/arpit04tripathi/files-cdn/raw/cdn/kafka/avro-overview.png)

![](https://github.com/arpit04tripathi/files-cdn/raw/cdn/kafka/avro-serialization.png)

```java
props.put("value.deserializer", "io.consfluent.kafka.serializers.KafkaAvroDeserializer");
props.put("schema.registry.url", "http://localhost:8081");
props.put("specific.avro.reader", "true");
```

-	Confluent Platform Quickstart
-	Confluent Platform – rpm packages by yum
-	Schema resolution

![](https://github.com/arpit04tripathi/files-cdn/raw/cdn/kafka/confluent-platform.png)
