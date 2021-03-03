---
layout: post
title: Producer API
permalink: /:collection/kafka/producer/api
---

-	bootstrap.servers = brokers list for zookeeper
-	Key.serializer
-	Value.serializer

KafkaProducer send(ProducerRecord<K,V> record) returns Future<RecordMetadata>, this acknowledgement contains partition id and offset number where partition resides.

![]({{site.cdn}}/kafka/producer-api.png)

-	Asynchronous Producer (Better throughput than fire-and-forget).
-	**max.in.flight.requests.per.connection** = number of in-flight messages sent to cluster without an acknowledgement.

```java
Properties props = new Properties();
props.put("bootstrap.servers", "localhost:9092, localhost:9093");
props.put("key.serializer", "org.apache.kafka.common.serialization.StringSerializer");
props.put("value.serializer", "org.apache.kafka.common.serialization.StringSerializer");
Producer<String, String> producer = new KafkaProducer<>(props);
ProducerRecord<String, String> record = new KafkaProducer<>(topic, key, value);
producer.send(record, new MyProducerCallback());
```
```
Class MyProducerCallback implements Callback{
@Override
Public void onCompletion(RecordMetadata recordMetadata, Exception e){
		If(e != null){ Sysout("AsynchronousProducer falied with exception"); }
	}
}
```
