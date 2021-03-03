---
layout: post
title: DDB Access Control
permalink: /:collection/aws/ddb/access-control
---

- Authentication and Access Control is managed using AWS IAM.
- Can create an IAM user with specific permissions to access and create dynamodb tables.
- Can create an IAM role which enables you to obtain temporary access keys to be used for accessing dynamoDB.
- Can also use special IAM Condition to restrict user access to only their records.

# IAM Condition Example
- Mobile gaming application with millions of users.
- User needs to access high scores for each game they are playing, access must be restricted so that they don't see anyone else's data.
- This can be done by adding a condition to an IAM Policy to allow access only to items where the partition key value matches their userID.
    - iam conditional parameter - dynamodb:LeadingKeys

![dynamodb-iam-condition]({{site.cdn}}/aws/ddb/dynamodb-iam-condition.png)

```cli
aws dynamodb get-item --table-name ProductCatalog --region eu-west-2 --key '{"id":{"n":"205"}}'
```
