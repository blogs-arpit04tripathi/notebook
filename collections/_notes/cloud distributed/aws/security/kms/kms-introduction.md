---
layout: post
title: KMS Introduction
permalink: /aws/kms/introduction
---

- KMS - Key Management System
- Managed service to create and control the encryption keys used to encrypt your data
- Integrates with EBS, S3, RedShift, Elastic Transcoder, WorkMail, RDS etc.
- Encryption Keys are Regional.

It is a good practice to create 2 different users
- KMSManager - who creates and manages the key
- KMSEncryptor - who has the ability to encrypt and decrypt4

![](https://github.com/arpit04tripathi/files-cdn/raw/cdn/aws/kms/kms-iam-dashboard.png)
