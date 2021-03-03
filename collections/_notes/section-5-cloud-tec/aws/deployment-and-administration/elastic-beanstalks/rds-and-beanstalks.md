---
layout: post
title: RDS and Beanstalks
permalink: /:collection/aws/beanstalks/rds-and-beanstalks
---

EBS (Beanstalks) supports 2 ways of integrating an RDS DB with your Beanstalk environment.
- **Launch within the EBS env**
  - Launch RDS instance from within EBS console ie. RDS instance created within your EBS environment - good option for Dev and Test env.
  - However it is not good for production environment because lifecycle of DB is tied to lifecycle of your application environment. If you terminate the envirinment, DB instance is also terminated.
- **Launch outside the EBS env**
  - For Production environments, preferred option is to decouple RDS instance from your EBS envirinment ie. launch outside EBS, directly from RDS section of aws console.
  - This option gives you more flexibility, allows you to connect multiple environments to the same DB, provides choice of wider types of DB types, and allows your to tear down your application environment without affecting the DB instance.

# Access to RDS from Beanstalks
To allow EC2 instances in EBS env to connect to outside DB, there are 2 additional configuration steps
- An additional security group must be added to your environment's autoscaling group.
- You need to provide connectino string configuration info to your application servers (endpoint, password using EBS env properties)
