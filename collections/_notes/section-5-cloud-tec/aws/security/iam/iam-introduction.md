---
layout: post
title: IAM Introduction
permalink: /:collection/aws/iam/introduction
---

- TOC
{:toc}

<hr><br>

# Introduction to IAM

What does IAM gives you?
* Allows you to manage users and their level of access to AWS console.
* Centralized control of your aws account
* Shared access to your aws account
* Granular Permissions
* Identity Federation(LDAP, Facebook, LinkedIn etc)
* MFA - Multifactor Authenticator, ex. username-password with token
* Provides temporary access to users.devices and services as necessary
* Allows you to setup your own password rotation policy
* Integrates with many aws services
* Supports PCI DSS Compliance for payment card services

# IAM Tems
* Users - End Users (people)
* Groups - Collection of users under one set of permissions
* Roles - Create roles and assign them to aws resources
* Policies - A document that defines one or more permissions

# Security Status Steps For new account

![iam-dashboard]({{site.cdn}}/aws/iam/iam-dashboard.png)

* Delete your root access keys
    - **Root Account** is the account created at the time of AWS Setup, it has complete admin access.
* Activate MFA on your root account
    - IAM Dashboard --> Activate MFA --> Google Authenticator
* Create individual IAM users
    - AccessKey and Access Secret 
        - For programatic login ie. access via APIs and Command Line.
        - visible only at the time of creation, after that you have to regenerate them in case you lost it.
    - Username and Password - Console login
    - New User have No Permission when first created.
* Use Groups to assign Permissions
    - Create Group --> GroupName --> Search s3 to add s3 read permission
    - User --> Groups Tab --> AssignGroup
* Apply IAM password policy.
    - Password policy --> set of rules
    - Can create custom password rotation policies.

```json
{
    "Version":"212-10-07",
    "Statement":[
        "Effect":"Allow",
        "Action":"*",
        "Resource":"*"
    ]
}
```

> ***IAM is universal***, doesn't apply to regions.

# Roles
* Roles --> Create Roles --> AWS Service --> Assign s3FullAccess permission --> roleName
* Grant permission to Application code running on an EC2 instance.

> ***Groups*** are for User, ***Roles*** are for entities
