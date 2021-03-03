---
layout: post
title: STS AssumeRoleWithWebIdentity
permalink: /:collection/aws/iam/sts-assumeRoleWithWebIdentity
---

- assume-role-with-web-identity is an API provided by STS (Security Token Service).
- Returns temporary security credentials for users authenticated by a mobile or web application or using a Web ID Provider like Amazon, Facebook or Google etc.
- For mobile applications, Cognito is recommended.
- Regular web applications can use STS assume-role-with-web-identity API.

![]({{site.cdn}}/aws/dev-theory/STS-AssumeRoleWithWebIdentity.png)

AWS Systems Manager Parameter Store provides secure, hierarchical storage for configuration data management and secrets management. You can store data such as passwords, database strings, and license codes as parameter values.
