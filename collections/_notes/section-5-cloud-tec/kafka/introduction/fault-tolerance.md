---
layout: post
title: Fault Tolerance
permalink: /:collection/kafka/fault-tolerance
---

Enabling a system to continue operating properly in the event of the failure of some of its components.

**Replication factor**
-	Number of total copies of a pertition.
-	3 is a reasonable number
-	Replication factor is set at a topic level

Replica created as Leader and Follower.

![]({{site.cdn}}/kafka/fault-tolerance.png)

Different **server.properties** used for each broker
-	broker.id=0 
-	log.dirs
-	broker port (1 machine for multiple brokers)

**ISR**
- in-sync replicas
- synced with leader.
