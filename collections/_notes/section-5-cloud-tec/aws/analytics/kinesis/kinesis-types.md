---
layout: post
title: Types of Kinesis
permalink: /:collection/aws/kinesis/types
---

- TOC
{:toc}

<hr><br>

# Kinesis Streams

- Kinesis data stream consists of shards
- A shard is a sequence of data records in a stream, each data record has a unique sequence number.
- Total capacity of stream is sum of individual capacities of shards.
- Single Shard Capacity
  - 5 transactions per second, upto max total data read rate 2MB per second.
  - upto 1000 records per second for writes, upto total data write rate of 1MB per second (including partition keys).
- As your data rate increases, you need to increase the number of shards (resharding).

![]({{site.cdn}}/aws/kinesis/kinesis-streams.png)

# Kinesis Firehose

- Don't have to worry about shards, streams or manually adding shards to keep up with your data.
- It is completely automated and you don't have to worry about consumers going in and mining that data as we can analyze data using lamda in realtime.
- Analysis step is optional.
- Analyzed data can be sent to S3 or to Elastic search clusture.
- No retention period as opposed to Kinesis Streams
- More automated way of doing kinesis

![]({{site.cdn}}/aws/kinesis/kinesis-firehose.png)

# Kinesis Analytics

- Kinesis Analytics lets you run SQL queries on that data as if it exists within firehose or streams then, you can use SQL query to store output data to S3. Redshift, Elastic Search Clusture etc.

![]({{site.cdn}}/aws/kinesis/kinesis-analytics.png)
