---
layout: post
title: Core APIs
permalink: /:collection/kafka/core-apis
---

- **Producer API** allows an application to publish a stream of records to one or more Kafka topics.
- **Consumer API** allows an application to subscribe to one or more topics and process the stream of records produced to them.
- **Streams API** allows an application to act as a stream processor, consuming an input stream from one or more topics and producing an output stream to one or more output topics, effectively transforming the input streams to output streams.
- **Connector API** allows building and running reusable producers or consumers that connect Kafka topics to existing applications or data systems. For example, a connector to a relational database might capture every change to a table.

![]({{site.cdn}}/kafka/kafka-components.png)

![]({{site.cdn}}/kafka/kafka-platform-capabilities.png)
