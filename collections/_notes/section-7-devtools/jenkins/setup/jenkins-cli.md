---
layout: post
title: Jenkins CLI
permalink: /:collection/jenkins/cli
---

**Why to use CLI ?**
- Easier, faster, efficient(memory management), continuous integration (setup build process)

- Start Jenkins => Java –jar Jenkins.war –httpPort=9080
- localhost:9080 > Manage Jenkins > Configure Global Security > enable security Checkbox > localhost:9080/cli > Download Jenkins cli jar from given hyperlink and place in any location > Got to specified location of cli jar > run the given command

```
java –jar Jenkins-cli.jar –s http://localhost:8080/ help
```

Enter passphrase > java –jar Jenkins-cli.jar –s http://localhost:8080/safe restart > Error regarding authorization > temporarily do Configure global security (Any one can do anything) > Safe restart
