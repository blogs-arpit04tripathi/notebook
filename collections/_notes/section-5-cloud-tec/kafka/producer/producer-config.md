---
layout: post
title: Producer Config
permalink: /:collection/kafka/producer/config
---

# bootstrap.servers
-	list of kafka broker url with port number.
-	necessary for producer to have connection with kafka clusture.
-	`props.put("bootstrap.servers", "localhost:9092, localhost:9093");`

# key.serializer
-	props.put("key.serializer", "org.apache.kafka.common.serialization.StringSerializer");

# value.serializer
-	props.put("value.serializer", "org.apache.kafka.common.serialization.StringSerializer");

# partitioner.class
-	For custom partitioner
-	props.put("partitioner.class", "SensorPartitioner");

# acks
-	0 – Producer doesn’t wait for response.
    -	Possible loss of messages
    -	High Throughout
    -	No Retries
-	1 – Producer waits for the response from leader
    -	Response as soon as leader receives the message, before replication.
    -	Possible to lose message if leader breaks before making replica.
    -	Not 100% reliable
-	all – Leader sends acknowledgement once all live replicas are in sync
    -	highest reliability
    -	highest latency
    -	here we can use asynchronous call

# retries
-	Defies number of times of retry for failure case.
-	Default value is 0
-	retry.backoff.ms – time between retries, default 100 ms.

# max.in.flight.requests.per.connection
-	number of messages allowed to sent without any acknowledgement, i.e. in-flight.
-	Bigger number increases throughput bult also bumps up the memory usage.

![]({{site.cdn}}/kafka/producer-with-callback.png)

# buffer.memory
# compression.type
# batch.size
# linger.ms
# client.id
# max.request.size
