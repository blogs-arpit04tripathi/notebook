---
layout: post
title: Version Control in Lambda
permalink: /:collection/aws/lambda/version-control
---

- Publish one or more versions of your lambda functions.
- Can work with different variations of your lambda function in development workflow, such as development, beta and production.
- Each lambda function version has a unique ARN(Amazon Resource Name).
- Once published a version, it is immutable(ie. it can't be changed).
- latest function code is maintained by AWS Lambda in $LATEST version.
- You can refer to this function by using ARN. There are two ARNs associated with initial version:
    - Qualified ARN - function ARN with version suffix
        - arn:aws:lambda:aws-region:acct-id:function:helloworld:$LATEST
    - UNQUALIFIED ARN - function ARN without the version suffix.
        - arn:aws:lambda:aws-region:acct-id:function:helloworld
- Alias - After creating version 1($LATEST), create alias PROD to point to version 1.
    - Once version 2 is published, update the alias PROD mapping to version 2.
    - In case of failure you can rollback to pred=vious version just by remapping the alias PROD.
- You can use versioning to split traffic for using BLUE-GREEN strategy

![]({{site.cdn}}/aws/serverlesl/../serverless/lambda-alias.png)
