---
layout: post
title: Restoring Backups
permalink: /aws/rds/restoring-backup
---

* Whenever you restore either an automatic backup or a manual snapshot, the restored version of the database will be a new RDS isntance with a new DNS endpoint.

```
original.eu-west-1.rds.amazonaws.com --> restored.eu-west-1.rds.amazonaws.com
```
