---
layout: post
title: DynamoDB Streams
permalink: /:collection/aws/ddb/streams
---

- Time-ordered sequence of item level modifications(insert, update, delete).
- Logs are encrypted at rest and stored for 24 hours.
- Used typically for auditing, archiving of transactions, replaying transactions to different tables, trigger events based on specific change within the dynamodb table.
- Good for serverless architectures, to trigger lambda functions or application to perform operations based on change in DynamoDB entry.
- Accessed using a dedicated endpoint.
- By default, primary key is recorded.
- Before and after images can be captured.

![dynamodb-streams-usecase]({{site.cdn}}/aws/ddb/dynamodb-streams-usecase.png)

# Processing DynamoDB Streams
- Events are recorded in near real-time.
- Applications can take actions based on contents.
- Event source for lambda.
- Lambda polls the dynamodb stream.
- Executes Lambda code based on a DynamoDB streams event.

![dynamodb-streams-usecase-trigger-workflow]({{site.cdn}}/aws/ddb/dynamodb-streams-usecase-trigger-workflow.png)
