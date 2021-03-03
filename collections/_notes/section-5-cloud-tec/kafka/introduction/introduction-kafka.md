---
layout: post
title: Kafka Introduction
permalink: /:collection/kafka/introduction
---

Apache Kafka® is a **distributed streaming platform**. What exactly does that mean?

A streaming platform has three key capabilities:
-	Publish and subscribe to streams of records, similar to a message queue or enterprise messaging system.
-	Store streams of records in a fault-tolerant durable way.
-	Process streams of records as they occur.

***What it can do?***
-	Can be used as an Enterprise messaging system.
-	Can be used for stream processing.
-	Provides connectors to import and export bulk data from DB and other systems.

**Kafka is generally used for two broad classes of applications**
-	Building real-time streaming data pipelines that reliably get data between systems or applications
-	Building real-time streaming applications that transform or react to the streams of data

**First a few concepts**
-	Kafka is run as a cluster on one or more servers that can span multiple datacenters.
-	The Kafka cluster stores streams of records in categories called topics.
-	Each record consists of a key, a value, and a timestamp.

**Kafka is**
- being used as big data streaming.
- scalable platform in terms of storing data and processing capacity.
- highly available
- popular for ***exactly once*** kind of scenarios, critical for financial domains.