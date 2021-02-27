---
layout: post
title: Change Home Directory
permalink: /:collection/jenkins/change-home-dir
---

- User Profile/.jenkins – contains info about logs, jobs, plugins, configuration etc.
- Why to change home directory – Default directory location is User profile. Have to move to disk where more memory space is available.

```
Cmd > go to Jenkins war > java –jar Jenkins.war
Go to local Jenkins > Manage Jenkins > Configure System > Check Home Directory
```

![jenkins-home-directory]({{site.cdn}}/devtools/jenkins/jenkins-home-directory.png)

Create new folder in required place > Copy everything from old directory to new one > Change the environment variable JENKINS_HOME to new directory

To restart - Localhost:8080/restart or through cmd prompt
Localhost:8080/systeminfo – To see summary of plugins, environment variables etc.
