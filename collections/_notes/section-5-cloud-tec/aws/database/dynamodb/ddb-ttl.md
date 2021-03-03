---
layout: post
title: DDB TTL
permalink: /:collection/aws/ddb/ttl
---

- Time To Live attribute defines an expiry time for your data.
- Expired items are marked for deletion, will be deleted within next 48 hours.
- Great for removing old or irrelevant data
    - session data
    - event logs
    - temporary data
- Reduces storage cost by automatically removing data which is no longer relevant.
- TTL is expressed in epoch time, seconds elapsed since Jan,1 1970 00:00.
- expiration time is set at the time of making the entry.
- When current time is greater than the TTL, the item will be expired and marked for deletion.
- You can filter out expired items from your queries and scans.

```
aws iam get-user

// Create SessionData table
aws dynamodb create-table --table-name SessionData --attribute-definitions \
AttributeName=UserID,AttributeType=N --key-schema \
AttributeName=UserID,KeyType=HASH \
--provisioned-throughput ReadCapacityUnits=5,WriteCapacityUnits=5

// Populate SessionData Table
aws dynamodb batch-write-item --request-items file://items.json
```

DynamoDB --> Table --> Actions --> TTL --> name of TTL attribute --> preview and save
