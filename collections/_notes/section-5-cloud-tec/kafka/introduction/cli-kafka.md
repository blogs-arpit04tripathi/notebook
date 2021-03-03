---
layout: post
title: Kafka CLI
permalink: /:collection/kafka/cli
---

- URL - https://kafka.apache.org/quickstart
- bin\windows\ instead of bin/, and change the script extension to .bat.

```java
// Unzip tar file
tar -xzf kafka_2.11-2.1.0.tgz
cd kafka_2.11-2.1.0
```

**Start Stop Zookeeper**
```
bin\windows\zookeeper-server-start.bat config/zookeeper.properties
bin\windows\zookeeper-server-stop.bat
```

**Start Kafka Cluster**
```
bin\windows\kafka-server-start.bat config/server.properties
bin\windows\kafka-server-stop.bat
```

**Create Topics**
```
bin\windows\kafka-topics.bat  --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic naruto
bin\windows\kafka-topics.bat --list --zookeeper localhost:2181
bin\windows\kafka-topics.bat --create --zookeeper localhost:2181 --replication-factor 3 --partitions 1 --topic my-replicated-topic
```

**Dashboard Describe**
```
bin\windows\kafka-topics.bat --describe --zookeeper localhost:2181 --topic my-replicated-topic
```

**Single Broker Cluster Consumer-Producer**
```
bin\windows\kafka-console-producer.bat --broker-list localhost:9092 --topic naruto
bin\windows\kafka-console-consumer.bat --bootstrap-server localhost:9092 --topic naruto --from-beginning
```

**Multiple Broker Cluster**
```cmd
cp config/server.properties config/server-1.properties
cp config/server.properties config/server-2.properties

config/server-1.properties:
    broker.id=1
    listeners=PLAINTEXT://:9093
    log.dirs=/tmp/kafka-logs-1
 
config/server-2.properties:
    broker.id=2
    listeners=PLAINTEXT://:9094
    log.dirs=/tmp/kafka-logs-2
	
bin/kafka-server-start.sh config/server-1.properties
bin/kafka-server-start.sh config/server-2.properties
```
