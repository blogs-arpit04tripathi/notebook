---
layout: post
title: EC2 Lab
permalink: /:collection/aws/ec2/lab
---

AWS Console --> Services --> EC2 --> Launch Instance --> Amazon Linux AMI --> t2 micro free tier --> configure instance details --> Add root storage --> Add tags --> Create instance

![ec2-config]({{site.cdn}}/aws/ec2/ec2-config.png)

Instance created from AMI (Amazon Machine Images)

Web Security Group 
- Virtual firewall, request come and go from here
- port 80 , tcp http
- port 22 , tcp ssh

Use Putty and PuttyKeyGen for connecting to EC2 instance.
- EC2 instance launch will prompt you for creating a private key .pem file.
- Putty needs .ppk (putty private key) file, so use PuttyGen.
- Open putty, 
    - hostname = ec-2-user@ipv4_address
    - Port 22
    - SSH --> Auth --> load private key
    - save and load

```linux
sudo su
yum update -y
yum install httpd -y // install apache to turn into web server
service httpd start
chkconfig httpd on // initiate httpd on instance restart
service httpd status
cd /var/www/html
ls
echo
```

# EC2 CLI
```ssh
ssh ec2-user@ec2_ip_address -i MyNewKeyPair.pem
sudo su
aws s3 ls
aws configure
    - Create IAM User with programatic access with User Group
aws s3 mb s3://acloudguru-rk
echo "hello cloudgurus" > hello.txt
aws s3 cp hello.txt s3://acloudguru-rk
```

* Always give your users the minimum amount of access required. (Least Privilege)
* Create groups and assign users to group.
* Secret Access Key (visible once on creation) and Access Key ID
* Create Access Credentials for each user rather than sharing single.

# EC2 WIth S3 Role
* Create IAM Role for EC2 --> Permissions for s3Full Access
* EC2 Instance --> Actions --> Instance Settings --> Attach/Replace IAM Roles --> Select EC2 Role

```java
cd ~/.aws   // home_directory/.aws
dir %UserProfile%\.aws  // Windows
```

* Roles allows you to not use access_key_id and secret_access_key
* ***Roles are preferred from Security perspective.***
* Roles are controlled by policies.
* You can change a policy on a role and it will take immediate affect.
* You can attach and detach roles to running EC2 instances without having to stop or terminate these instances.
