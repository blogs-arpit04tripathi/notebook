---
layout: post
title: DDB Tables
permalink: /:collection/aws/ddb/tables
---

- Stored on SSD storage (Solid State Disks)
- Spread across 3 geographically distinct data centers
- Choice of 2 consistency Models:
    - Eventual Consistent Reads (default)
        - Consistency across all copies of data is usually reached within a second.
        - Repeating a read after a short timeshould return the updated data. (best read performance)
    - Strongly Consistent Reads
        - returns a result that reflects all writes that received a successful response prior to the read.

* Dynamo DB
    - Table
    - Items (row of a table)
    - Attributes (column in a table)
    - Supports key-value and document data-structures
        - key = name of data
        - value = data itself
        - Documents can be written in json, html or xml
