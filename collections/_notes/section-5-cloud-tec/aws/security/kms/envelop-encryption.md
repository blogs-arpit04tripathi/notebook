---
layout: post
title: Envelope Encryption
permalink: /:collection/aws/kms/envelop-encryption
---

Customer Master Key
- used to decrypt the data key (envelope key)
- evelope key is used to decrypt the data

Deleting KMS CMK will take anywhere between 7-30 days as per selection made by user.

![]({{site.cdn}}/aws/kms/envelope-encryption.png)
