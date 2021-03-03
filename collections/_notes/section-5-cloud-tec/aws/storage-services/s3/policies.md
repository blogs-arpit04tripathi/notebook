---
layout: post
title: S3 Policies
permalink: /:collection/aws/s3/policies
---

- TOC
{:toc}

---


```
AWS --> S3 --> Shows global view of all regions --> select region --> Create bucket --> can create folders
```
- Enable Versioning Checkbox
- Enable Server Access Logging
- Can use tags to track project costs.
- Enable object level logging using AWS cloudTrail
- Enable Default Encryption
    - AES-256 : Uses server side encryption with Amazon S3-Managed Keys (SSE-S3)
    - AWS-KMS : Uses Server Side Encryption with AWS KMA-Managed Keys(SSE-KMS)
- CloudWatch request metrics

```
Select Folder --> upload files -->
```
- Set permissions
- can set encryption

# Bucket Public Settings

```
select bucket --> Permissions --> 
```
![bucket-permissions-public-settings]({{site.cdn}}/aws/s3/bucket-permissions-public-settings.png)

* If bucket policy is set as private, you cannot upload public objects to it.

# Bucket Policy

- Use policy generator to create document.
- Policy Type - SQS, S3, VPC, IAM, SNS Topic
- Effect - Allow, Deny
- Principal - User (ARN), S3 Service, AWS account number etc. (Entity for policy)
- Action - action for AWS Service
- ARN (Amazon Resource Name) - bucket ARN (target object)
- Click Add Statement to add policy statement, can add multiple statements
- Click Generate policy
- Copy paste the policy to bucket --> permissions --> bucket policy

![bucket-permissions-policies]({{site.cdn}}/aws/s3/bucket-permissions-policies.png)

