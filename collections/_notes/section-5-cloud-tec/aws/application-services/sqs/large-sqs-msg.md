---
layout: post
title: Messaging Large SQS Messages
permalink: /:collection/aws/sqs/large-sqs-msg
---

- For large SQS messages - 256KB upto 2GB.
- Use S3 to store the messages.
- Use Amazon SQS Extended client library for Java to manage them.
- AWS SDK for java provides an api for S3 bucket and object operations.

SQS Extended Client Library for java allows you to
- Specify that messages are always stored in S3 for only messages > 256KB
- Send a message which references a message object stored in S3.
- Get a message object from S3.
- Delete a message object for S3.

![]({{site.cdn}}/aws/sqs/large-sqs-messages.png)

For Large SQS
- You need
  - AWS SDK for java
  - SQS extended client library for java
  - S3 bucket
- You can't use
  - AWS CLI
  - AWS Management Console/ SQS console
  - SQS API
  - Any other AWS SDK