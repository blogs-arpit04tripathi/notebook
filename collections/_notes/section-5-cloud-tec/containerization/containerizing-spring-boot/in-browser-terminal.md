---
layout: post
title: Accessing the In-Browser Terminal for the Running Containers
permalink: /:collection/containerization/docker/in-browser-terminal
---

You can open a command prompt on any running container on OpenShift. Let’s open a terminal on MySQL so we can check if the database has been created and the values has been imported.

To open a terminal, click the pod number for your MySQL application that you see in the **Overview** page. This will open a page containing the details of your pod, which is how Kubernetes/OpenShift refers to the group of containers that run together. Once you click the **Terminal** tab, you will see a web terminal open in the running container *mysql*.

The credentials (username and password) in the MySQL container are stored in environment variables. You can connect to MySQL Server executing mysql -uecho $MYSQL_USER--password=echo $MYSQL_PASSWORD-h 127.0.0.1 catalog, as you can see below:
```
sh-4.2$ mysql -u `echo $MYSQL_USER` --password=`echo $MYSQL_PASSWORD` -h 127.0.0.1 catalog
mysql: [Warning] Using a password on the command line interface can be insecure.
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 1307
Server version: 5.7.21 MySQL Community Server (GPL)
Copyright (c) 2000, 2018, Oracle and/or its affiliates. All rights reserved.
Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.
Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
mysql>
```

Once you are connected, you can check the values in the database.
```sql
mysql> show tables;
+-------------------+
| Tables_in_catalog |
+-------------------+
| PRODUCT           |
+-------------------+
1 row in set (0.00 sec)
mysql> select * from PRODUCT;
. . .
8 rows in set (0.00 sec)
mysql> exit
Bye
sh-4.2$
```
