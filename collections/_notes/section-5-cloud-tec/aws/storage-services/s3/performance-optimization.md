---
layout: post
title: S3 Performance Optimization
permalink: /:collection/aws/s3/performance-optimization
---

- By default, designed to support very high request rates.
- However, if S3 buckets are routinely receiving >100 PUTS/LIST/DELETE or >100 GET requests per second, then there are some best practice guidelines to optimize S3 performance.
- Guidance is based on type of workload you are running
    - **GET-Intensive Workloads** - Use CloudFront content delivery service to get best performance. CloudFront will cache your most frequently accessed objects and will reduce latency for your GET requests.
    - **Mixed Request Type Workloads** - a mix of GET, PUT, DELETE
        - the key names being used for your objects impact performance for intensive workloads.
        - S3 uses keyname to determine which partition an object will be stored in.
        - Use of sequencial keynames eg. name prefixed with timestamp or alphabetical sequence increases the likelihood of having many objects stored on same partition.
        - For heavy workloads this can cause I/O issues and contention.
        - By using random prefix (like hex hash) to the key names, you can force S3 to distribute your keys accross multiple partitions, distributing the I/O workload.
- S3 performance updates
    - 3,500 PUT requests per second
    - 5.500 GET requests
    - This negates the previous guidance to randomize your object names, now sequencial and logical naming patterns can used without any performance implications.
