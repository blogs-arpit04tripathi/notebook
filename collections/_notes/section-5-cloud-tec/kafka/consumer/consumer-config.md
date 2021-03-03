---
layout: post
title: Consumer Config
permalink: /:collection/kafka/consumer/config
---

```java
Properties props = new Properties();
props.put("bootstrap.servers", "localhost:9092");
props.put("group.id", "consumer-tutorial");
props.put("key.deserializer", StringDeserializer.class.getName());
props.put("value.deserializer", StringDeserializer.class.getName());
KafkaConsumer<String, String> consumer = new KafkaConsumer<>(props); 
```
we need to configure an initial list of brokers for the consumer to be able discover the rest of the cluster. This doesn’t need to be all the servers in the cluster—the client will determine the full set of alive brokers from the brokers in this list.
```java
consumer.subscribe(Arrays.asList("foo", "bar"));
```
After you have subscribed, the consumer can coordinate with the rest of the group to get its partition assignment. it is not possible to mix automatic and manual assignment. The subscribe method is not incremental: you must include the full list of topics that you want to consume from. You can change the set of topics you’re subscribed to at any time–any topics previously subscribed to will be replaced by the new list when you call subscribe.

After subscribing to a topic, you need to start the event loop to get a partition assignment and begin fetching data. It sounds complex, but all you need to do is call poll in a loop and the consumer handles the rest. Each call to poll returns a (possibly empty) set of messages from the partitions that were assigned.
```java
try {
  while (running) {
    ConsumerRecords<String, String> records = consumer.poll(1000);
    for (ConsumerRecord<String, String> record : records)
      System.out.println(record.offset() + ": " + record.value());
  }
} finally {
  consumer.close();
}
```
The poll API returns fetched records based on the current position. When the group is first created, the position will be set according to the reset policy (which is typically either set to the earliest or latest offset for each partition). Once the consumer begins committing offsets, then each later rebalance will reset the position to the last committed offset. The parameter passed to poll controls the maximum amount of time that the consumer will block while it awaits records at the current position. The consumer returns immediately as soon as any records are available, but it will wait for the full timeout specified before returning if nothing is available.

You should always close the consumer when you are finished with it. Not only does this clean up any sockets in use, it ensures that the consumer can alert the coordinator about its departure from the group. 

-	heartbeat.interval.ms
-	session.timeout.ms
