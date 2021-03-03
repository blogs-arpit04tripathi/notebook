---
layout: post
title: Consumer API
permalink: /:collection/kafka/consumer/api
---

![]({{site.cdn}}/kafka/consumer-group-partition-mapping.png)

-	Consumer Groups are used to read and process the data in parallel for an application.
-	Max active consumers in a group = no. of partitions.
-	Partitions are never shared among the members of same group at the same time.
-	Group coordinator maintains a list of active consumers.
-	Rebalance is initiated when the list of consumers is modified.
-	Group Leader executes a rebalance activity.

Consumer group co-ordinator is one of broker while group leader is one of consumer in consumer group.

Group co-ordinator is nothing but one of brokers which receives heartbeats(or polling for message) from all consumers of a consumer group. Every consumer group has a group coordinator. If consumer stops sending heartbeats, coordinator will trigger rebalance.

When a consumer wants to join a consumer group, it sends a JoinGroup request to the group coordinator. The first consumer to join the group becomes the group leader. The leader receives a list of all consumers in the group from the group coordinator (this will include all consumers that sent a heartbeat recently and are therefore considered alive) and it is responsible for assigning a subset of partitions to each consumer. It uses an implementation of PartitionAssignor interface to decide which partitions should be handled by which consumer. After deciding on the partition assignment, the consumer leader sends the list of assignments to the GroupCoordinator which sends this information to all the consumers. Each consumer only sees his own assignment - the leader is the only client process that has the full list of consumers in the group and their assignments. This process repeats every time a rebalance happens.

The coordinator is responsible for managing the state of the group. Its main job is to mediate partition assignment when new members arrive, old members depart, and when topic metadata changes. The act of reassigning partitions is known as rebalancing the group.

When a group is first initialized, the consumers typically begin reading from either the earliest or latest offset in each partition. The messages in each partition log are then read sequentially. As the consumer makes progress, it commits the offsets of messages it has successfully processed. For example, in the figure below, the consumer’s position is at offset 6 and its last committed offset is at offset 1.

![]({{site.cdn}}/kafka/consumer-offset-illustration.png)

When a partition gets reassigned to another consumer in the group, the initial position is set to the last committed offset. If the consumer in the example above suddenly crashed, then the group member taking over the partition would begin consumption from offset 1. In that case, it would have to reprocess the messages up to the crashed consumer’s position of 6.

The diagram also shows two other significant positions in the log. The log end offset is the offset of the last message written to the log. The high watermark is the offset of the last message that was successfully copied to all of the log’s replicas. From the perspective of the consumer, the main thing to know is that you can only read up to the high watermark. This prevents the consumer from reading unreplicated data which could later be lost.
