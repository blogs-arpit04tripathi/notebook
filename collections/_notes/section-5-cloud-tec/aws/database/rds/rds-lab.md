---
layout: post
title: RDS Lab
permalink: /:collection/aws/rds/lab
---


AWS Services --> RDS --> Create DB --> will get dns rather than ip address
- Amazon Aurora not available in free tier
- VPC Security Group

EC2 --> Advanced Details --> Add Bootsrap Scripts

* Bootstrap scripts starts with shabang #!
```
#!/bin/bash
yum install httpd php-mysql -y
yum update -y
chkconfig httpd on
service httpd start
...
```

* RDS in one Security Group while EC2 in other Security Group, how to communicate?
    - Open port 3306 in RDS to EC2 security group as communication is EC2 -> RDS
    - Add SG to inbound value
