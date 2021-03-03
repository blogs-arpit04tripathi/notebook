---
layout: post
title: KMS API Calls
permalink: /:collection/aws/kms/api-calls
---

```
aws kms encrypt --key-id <YourKeyId> --plaintext fileb://secret.txt --output text --query CiphertextBlob | base64 --decode > encryptedsecret.txt
```
```
aws kms decrypt --ciphertext-blob fileb://encryptedsecret.txt --output text --query Plaintext | base64 --decode > decryptedsecret.txt
```
```
aws kms re-encrypt --destination-key-id <YourKeyId> --ciphertext-blob fileb://encryptedsecret.txt | base64 > newencryptedsecret.txt
```
```
aws kms enable-key-rotation --key-id <YourKeyId>
```
