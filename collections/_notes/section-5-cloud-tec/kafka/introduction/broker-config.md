---
layout: post
title: Kafka Broker Configuration
permalink: /:collection/kafka/broker-config
---

|Broker Configuration||
|---|---|
|broker.id|	id of broker|
|port|	port on which broker runs, needs to be changed if more than 1 broker is on same machine.|
|log.dirs|	directory where logs for the broker will be published.|
|zookeeper.connect|	zookeeper address, necessary to form a clusture.|
|delete.topic.enable|	Default false. Required for Dev environments. topic management tool.|
|auto.create.topics.enable|	Default false. Required for Dev environments. Non-existing topic gets created if something published on such topic.|
|default.replication.factor|	Default value is 1.|
|num.partitions|	Default value is 1.|
|log.retention.ms|	Deafault 7 days. Older messages get deleted from kafka.|
|log.retention.bytes|	Partition size for cleanup activity. Applicable to partition only.|
