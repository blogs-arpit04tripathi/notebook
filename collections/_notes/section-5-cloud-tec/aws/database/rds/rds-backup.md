---
layout: post
title: RDS Backups
permalink: /:collection/aws/rds/backup
---

* Two types of backups
    - Automated Backups
    - Database Snapshots

# Automated Backups
- Allow to recover your DB to any point in time within **retention period**
- retention period can be between 1 and 35 days.
- Takes full daily snapshots and also stores transaction logs throughout the day.
- When you do recovery, AWS first choose most recent daily backup, and then apply transaction logs relevant to that day. This allows you to point down the recovery upto specific second in time, within retention period.
- enabled by default.
- backup data stored in s3.
- free storage equals to size of DB ie. 10 Gb RDS instance will have 10 Gb sorage on s3.
- Backups are taken within defined window.
- During backup window, storage I/O may be suspended while your data is being backed-up and you may experience elevated latency.
- Deleting RDS instance also deletes Automated backup.

# Snapshots
- DB snapshots are done manually ie. user initiated.
- They are stored even after you delete the original RDS instance, unlike automated backups.
