---
layout: post
title: RDS Multi-AZ
permalink: /:collection/aws/rds/multi-az
---

![multi-az]({{site.cdn}}/aws/ec2/multi-az.png)

* Multi-AZ allows you to have an exact copy of your production database in another availabilty zone. (Standby DB)
* AWS handles the replication for you, write to production database is automatically synchronized to the standby database.
* For planned DB maintenance event, DB instance failure, or Availability Zone failure, amazon RDS will automatically failover to standby so that DB operations can resume quickly without administrative intervention. For this reason we deal with DNS name rather than ip-addresses.
* ***Multi-AZ is for Disaster Recovery only, For performance improvement use Read Replicas***
* Multi-AZ Databases - SQL Server, Oracle, MySQL Server, PostgreSQL, MariaDB

# Read Replicas

![read-replica.png]({{site.cdn}}/aws/ec2/read-replica.png)

* Allow you to have read-only copy of your production DB.
* Achieved by using Asynchronous replication from the primary RDS instance to the read replica.
* Used primarily for very read-heavy database workloads.
* Available for - MySQL Server, PostgreSQL, MariaDB, Aurora.
* Used for scaling, not for Disaster Recovery.
* Must have automatic backups turned on in order to deploy read replicas.
* Can have upto 5 read replica copies of any DB.
* You can have read replicas of read replicas, with some latency.
* Each read replica will have its own DNS endpoint.
* You can have read replicas that have Multi-AZ.
* You can create read replicas of Multi-AZ source DB.
* Read replicas can be promoted to be their own DB, this breaks the replication.
* You can have read replicas in a different region.
* Can enable encryption on read replicas even if source RDS instance is not encrypted.

# How to create Read Replica?
	- Step 1 : AWS console > RDS > Select instance 
    - Create Read Replica : Step 1 > Instance Actions > Create read replica
    - Apply Multi-AZ : Step 1 > Instance Action > Modify > check multi-az as yes.

![read-replica-encrypt.png]({{site.cdn}}/aws/ec2/read-replica-encrypt.png)
