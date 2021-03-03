---
layout: post
title: Encryption
permalink: /:collection/aws/rds/encryption
---

* Encryption at rest is supported for MySQL, Oracle, SQL Server, PostgreSQL, MariaDB and Aurora.
* Encryption done using AWS Key Management Service(KMS).
* Once RDS instance is encrypted, it applies to
    - data stored at rest in the underlying storage
    - Automated Backups
    - Read replicas
    - Snapshots
* Encrypting existing DB is not yet supported
    - Create snapshot, make a copy of the snapshot and encrypt the copy, then restore it.

```
RDS --> Instance Actions --> Create replicas or restore
RDS --> Snapshots --> Actions --> Copy --> Enable Encryption
```
