---
layout: post
title: AppSpec File
permalink: /:collection/aws/devtools/appSpec-file
---

- Configuration file defining parameters to be used during CodeDeploy deployment.
- For EC2 and On-Premise systems, YAML only.
- Lambda - YAML and JSON supported.
- File structure depends on whether you are deploying on EC2 or Lambda.

# EC2 AppSpec File
- version
  - reserved for future use.
  - currently allowed value is 0.0
- OS - Operating system version being used eg. linux or windows.
- files
  - configuration files, packages.
  - location of any application file that needs to be copied and where they need to be copied to.
- hooks
  - lifecycle hooks
  - scripts to run at certain point during the deployment lifecycle.
  - Hooks have a very specific run order.

**Example of scripts**
- unzip files - unzip application files prior to deployment.
- run tests - run functional tests on newly deployed application.
- deal with load balancing - de-register and re-register instances with load balancer.

![]({{site.cdn}}/aws/dev-theory/appspec-yaml.png)

**Typical Folder Setup**
- /Scripts
- /Config
- /Source
- appspec.yml must be placed in root directory otherwise deployment will be failed.

![]({{site.cdn}}/aws/dev-theory/code-deploy-lifecycle.png)
