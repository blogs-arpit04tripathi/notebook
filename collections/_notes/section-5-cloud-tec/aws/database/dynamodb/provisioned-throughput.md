---
layout: post
title: DDB Provisioned Throughput
permalink: /:collection/aws/ddb/provisioned-throughput
---

- TOC
{:toc}

<hr><br>


# Provisioned Throughput
- Mechanism to define capacity and performance requirements in DynamoDB.
- DynamoDB provisioned Throughput is measured in Capacity Units.
- At time of creating table you specify - Read Capacity Units and Write Capacity Units.
```
1 Write Capacity Units = 1 x 1KB Write per second
```
```
1 Read Capacity Unit = 1 x Strongly Consistent Read of 4KB per second
OR
2 x Eventually Consistent Read of 4KB per second. (default)
```

Example - RCU to KB - 5 RCU and 5 WCU
```
5 RCU   = 5 x 4 ie. 20 KB strongly consistent read
        = 5 x 2 x 4 ie. 40 KB eventually consistent read

5 WCU   = 5 x 1 ie. 5 KB write per second
```
Example - KB to RCU - 80 items per second with 3KB each, strongly consistent reads required
```
3KB/4KB = 0.75, rounded to ceil integer ie. 1 RCU.
80 items per second ==> 80 RCU
// For eventually consistent
Divide 80 by 2, ie. 40 RCU eventual consistency as it has 2 x 4KB reads per second
```
Example - KB to RCU - Write 100 items per second, 512 bytes size
```
512 bytes/1KB = 0.5, rounded to ceil integer ie. 1 WRU
100 Writes per second ==> 100 WCU
```

# Provisioned Throughput exceeded and Exponential Backoff
- ProvisionedThroughputExceededException
- Your request rate is too high for read/write capacity provisioned on your DynamoDB table.
- SDK will automatically retry the request until successful.
- If you are not using SDK, you can:
    - Reduce request frequency.
    - Use Exponential Backoff.

### Exponential Backoff
- Many components ina network can generate errors due to being overloaded.
- In addition to simple retries, all aws sdk use Exponential Backoff.
- Progressively longer waits between consecutive retries eg. 50ms, 100ms, 200ms .. for improved flow control.
- If after 1 minute this doesn't work, your request size may be exceeding the throughput for your read/write capacity.
- This feature is not just for DynamoDB, it is available for every aws sdk and applies to many services within aws eg. s3 buckets, cloudFormation, SES.
