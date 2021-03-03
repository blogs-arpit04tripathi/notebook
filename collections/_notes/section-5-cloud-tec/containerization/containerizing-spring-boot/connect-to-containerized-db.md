---
layout: post
title: Connecting Your Containerized Application to a Containerized Database
permalink: /:collection/containerization/docker/connect-to-containerized-db
---

The application that you forked from https://github.com/rafabene/refcard-demo contains an endpoint that replies with a catalog of items, their names, and their prices in JSON format. These values are stored in an H2 “in-memory” database.

You can check this endpoint by opening the http:///api/catalog/ endpoint in the browser.

However, an in-memory database is not suitable for Enterprise applications. To replace our H2 database, we need to deploy a MySQL database. Because of the quota limit, before creating the database, make sure that you have only one replica of your refcard-demo application running.

In **Search Catalog**, select **MySQL**. On the wizard screen, change the value of *MySQL Database Name to catalog*. The other values like “username” and “password” can be generated automatically so you can see how your application can consume those generated values later.

![]({{site.cdn}}/webservices/docker/mysql-config.png)

Click Create.

MySQL will be deployed, and all the sensitive information is stored in a “secret” object. This object can be consumed by the refcard-demo application as an environment variable or as a volume.

To configure our refcard-demo application to point to this MySQL instance, click **Deployment Config** for *refcard-demo*. Under the **Environment** tab, add the following values:
-	**SPRING_DATASOURCE_URL**: jdbc:mysql://mysql/catalog?useSSL=false
-	**SPRING_DATASOURCE_DRIVER_CLASS_NAME**: com.mysql.jdbc.Driver

Now, click Add ValueFrom Config Map or Secret and add:
-	**SPRING_DATASOURCE_USERNAME**: mysql (secret) / database-user
-	**SPRING_DATASOURCE_PASSWORD**: mysql (secret) / database-password

Click **Save**. Because these environment variables were introduced, OpenShift will replace the existing replica with a new one containing these values. After the deployment, you can check your application at http:///api/catalog/ to verify that it’s working.

According to Spring Boot configuration, these environment variables have a higher preference to configure the application over the existing application.properties file that already exists in the application.

We don’t know the value of the generated username and password for MySQL. However, we could configure the application to read the sensitive values from the “secret” object called mysql that was created when we deployed the database.
