---
layout: post
title: CMK - Customer Master Key
permalink: /:collection/aws/kms/cmk
---

- Customer Master Key
  - alias
  - create date
  - description
  - key state
  - key material(either customer provided or AWS provided)
- can never be exported
  - need to use cloud HSM
- KMS uses multitenancy hardware, cloud HSM is dedicated to you.

# Setup a CMK
- Create alias and descritpion
- Choose Key Material Option - KMS or external
- Define Key Administrative Permissions
  - IAM Users/Roles that can administer(but not use) the Key through the KMS API.
- Define Key Usage Permissions
  - IAM Users/Roles that can use the key to encrypt/decrypt data.
