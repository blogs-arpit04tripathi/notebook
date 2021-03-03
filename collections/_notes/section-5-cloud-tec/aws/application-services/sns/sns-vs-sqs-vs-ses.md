---
layout: post
title: SNS vs SQS vs SES
permalink: /:collection/aws/sns/sns-vs-sqs-vs-ses
---

# SNS vs SQS
- Both are messaging services in AWS.
- SNS is Push, SQS is poll (pull)

# SES vs SNS
- SES(Simple Email Service) is scalable and highly available email service.
- Can also be used to receive emails, these can be stored in S3 bucket.
- Incoming emails can be used to trigger lambda functions and SNS notifications.
