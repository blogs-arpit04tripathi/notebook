---
layout: post
title: Custom Partitioner
permalink: /:collection/kafka/partitioner/custom
---

- [ApacheKafkaTutorials](https://github.com/LearningJournal/ApacheKafkaTutorials)

```java
props.put("partitioner.class", "SensorPartitioner");
props.put("speed.sensor.name", "TSS"); ------------------------> Custom property, not provided by kafka
```

```java
public class SensorPartitioner implements Partitioner {
    // First 30% for specific partition
    private String speedSensorName;

    public void configure(Map < String, ? > configs) {
        speedSensorName = configs.get("speed.sensor.name").toString();
    }

    public int partition(String topic, Object key, byte[] keyBytes, Object value,
        byte[] valueBytes, Cluster cluster) {
        List < PartitionInfo > partitions = cluster.partitionsForTopic(topic);
        int numPartitions = partitions.size();
        int sp = (int) Math.abs(numPartitions * 0.3);
        int p = 0;
        if ((keyBytes == null) || (!(key instanceof String)))
            throw new InvalidRecordException("All messages must have string key");
        if (((String) key).equals(speedSensorName))
            // key is same hence hashing the value for partition number
            p = Utils.toPositive(Utils.murmur2(valueBytes)) % sp;
        else
            p = Utils.toPositive(Utils.murmur2(keyBytes)) % (numPartitions - sp) + sp;
        System.out.println("Key = " + (String) key + " Partition = " + p);
        return p;
    }
    public void close() {}
}
```
