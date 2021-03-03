---
layout: post
title: RebalanceListener
permalink: /:collection/kafka/consumer/rebalance-listner
---

**HOW TO KNOW THAT A REBALANCE IS TRIGGERED?**
- Consumer RebalanceListener
- onPartitionsRevoked() -  
- onPartitionsAssigned() – called after partition is assigned and before reading of messages start.

**Responsibilities of ConsumerRebalanceListener**
-	Maintain a list of offsets that are processed and ready to be committed.
-	Commit the offsets when partitions are going away.

![]({{site.cdn}}/kafka/rebalance-triggered.png)

```java
RebalanceListner rebalanceListener = new RebalanceListner(consumer);
Consumer.subscribe(Arrays.asList(topics), rebalanceListener);
...
for(ConsumerRecord<String, String> record : records){
	rebalanceListner.addOffset(record.topic(), record.partition(), record.offset())f
}
consumer.commitSync(rebalanceListner.getCurrentOffsets);

public class RebalanceListner implements ConsumerRebalanceListner{
	private KafkaConsumer consumer;
	private Map<TopicPartition, OffsetAndMetadata> currentOffsets = new HasMap();
}
```

Things handled by kafka are
-	Automatic group management and partition assignment
-	Offset and consumer positions control.

Automatic Partition Assignment - You don’t know which partition goes to which consumer.

![]({{site.cdn}}/kafka/commit-specific-offset-example.png)

Commit in 
- Range (first 3 partitions for example)
- Round Robin
