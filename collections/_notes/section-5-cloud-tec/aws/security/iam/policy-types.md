---
layout: post
title: Types of IAM Policies
permalink: /:collection/aws/iam/policy-types
---

IAM (Identity Access Management) is used to define user access permissions within AWS.

There are 3 types of policies
- Managed Policies
- Customer Managed Policies
- Inline Policies

# Managed Policies
- A Managed Policy is an IAM policy which is created and administered by AWS.
- AWS provide Managed Policies for common use cases based on job function eg. AmazonDynamoDBFullAccess, AWSCodeCommitPowerUser, AmazonEC2ReadOnlyAccess etc.
- These aws provided policies allow you to assign appropriate permissions to your users, groups and roles without having to write the policy yourself.
- A Single managed policy can be attached to multiple users, groups or roles within the same AWS account and across different accounts.
- You cannot changes the permimssions defined in an AWS amanged policy.

# Customer Managed Policy
- A standalone policy that you create and administer inside your own aws account. You can attach this policy to multiple users, groups and roles- but within your own account.
- You can copy any managed policy and customize it to fit your organization requirements.
- Recommended for use cases where managed poicies don't meet needs of your environment.

# Inline Policies
- Embedded within the user, group or role to which it applies.
- Strict 1:1 relation between the entity and policy.
- When you delete the user, group or role with embedded policy, the policy will also be deleted.
- AWS recommends Managed Policies over Inline Policies.
- Used when you want to be sure that the permissions in a policy are not inadvertently assigned to any other user, group or role than the one they are intended for.
