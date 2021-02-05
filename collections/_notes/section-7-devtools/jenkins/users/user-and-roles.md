---
layout: post
title: Create Users and Manage Roles
permalink: /:collection/jenkins/user-and-roles
---

Run Jenkins.war > java –jar Jenkins.war –httpPort=9080
Local:9080 > Login as Admin > Manage Jenkins > Manage users > Create User > Login with New user > Hover Logged in User (Configure)

Admin Password => Home Directory / secrets / initialAdminPassword

- For creating user roles, use Roles Strategy Plugin (.hpi file).
- HomeDirectory/Plugins – copy here and restart
- localhost:9080 > Manage Jenkins > Manage Plugins > goto Available tab and search for it 
OR
localhost:9080 > Manage Jenkins > Manage Plugins > goto Advance tab and upload .hpi

# Steps To Create Roles

Now Login as Admin > Manage Jenkins > configure Global Security > Enable security checkbox > Authorization (Role Based Strategy)

- Global Roles – (employee)
  - Login as Admin > Manage Jenkins > Manage and Assign Roles > Manage Roles > Global Roles (Overall Read and view)
- Project Roles – (Dev)
  - Login as Admin > Manage Jenkins > Manage and Assign Roles > Manage Roles > Project Roles > Developer (pattern = Dev.*) > Apply

Pattern – Pattern in name of project 

**Types of roles in Manage and Assign Roles**
1. Global Roles
2. Project Roles
3. Slave Roles

# Steps To Assign Roles

Login as Admin > Manage Jenkins > Manage and Assign Roles > Assign Users > Add User to global Roles (employee) > Apply

Login as Admin > Manage Jenkins > Manage and Assign Roles > Assign Users > Add User to Project Roles (Dev or Test) > Apply
