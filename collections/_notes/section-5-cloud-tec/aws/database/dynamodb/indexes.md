---
layout: post
title: Indexes
permalink: /:collection/aws/ddb/indexes
---


- In SQL DB, index is a data structure which allows you to perform fast queries on speccific columns that you want to include in index and run your queries on index rather than entire dataset.
- Types of Index in DynamoDB for fast queries
    - Local Secondary Index
    - Global Secondary Index

# Local Secondary Index
- can only be created when you are creating your table
- cannot add, remove or modify it later
- has same partition key as your original table, but a different sort key
- Gives you a different view of data organized according to an alternative sort key.
- Any queries based on this sort key are much faster using the index then main table.
- ex. partition key = userID, sort key = account creation date

# Global Secondary Index
- can create when you create a table or add it later.
- different partition keys as well as different sort key.
- gives a completely different view of data
- speeds up any queries relating to this alternative partition and sort key
- ex. partition key = email address, sort key = last login date

![index-types]({{site.cdn}}/aws/ddb/index-types.png)
