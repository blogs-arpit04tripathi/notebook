---
layout: post
title: DDB Primary Keys
permalink: /:collection/aws/ddb/primary-keys
---

- TOC
{:toc}

---

* DynamoDB stores and retrieves data based on a primary key
* Two types of primary key
    - partition key
    - sort key

# Partition Key - Unique Attribute (eg. user ID)
- value of partition key is input to an internal hash function which determines partition or physical location on which the data is stored.
- if you are using partition key as primary key, then no 2 items can have the same partition key.

# Composite Key
- Partition Key + Sort Key
- example - same user posting multiple times in a forum
- primary key = userID (partition key) + timestamp (sort key)
- All items with same partition key are stored together; then sorted according to sortKey value.
- Allows you to store multiple items with same partition key.
