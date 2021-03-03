---
layout: post
title: CICD
permalink: /:collection/aws/devtools/cicd
---

- Software industry best practice.
- Continuous Integration Continuous Delivery/Deployment

# Benefits of CICD Approach
- Automation is good - Fast, repeatable, scalable, enables rapid deployment.
- Manual is bad - Slow, error prone, inconsistent, unscalable, complex.
- Small Changes - Test each code change and catch bugs while they are small and simple to fix.

# Continuous Integration Workflow
- Shared code repository - Multiple developers contributing to a shared code repository like git. Frequently merging or integrating code updates.
- Automated Build - When changes appear in the code repository, this triggers an automated build of the new code.
- Automated Test - Run automated tests to check the code locally before it is committed into the master code repository.

# Continuous Delivery and Deployment Workflow
- Code is Merged - After successful tests, the code gets merged to the master repository.
- Prepared for Deployment - Code is biuld, tested and packaged for deployment.
- **Manual Decision** - Humans involved in decision to deploy the code. Continuous Delivery.
- or **Fully Automated** - System deploys the code as soon as it is ready for deployment. This is known as Continuous Deployment.
