---
layout: post
title: Configuring Beanstalks
permalink: /:collection/aws/beanstalks/config
---

- EBS can be configured by using EBS configuration file.
- eg. you can define packages to install, create linux users and group, run shell commands, specify services to enable or configure your load balancer etc.
- These are yaml files or json files
- can have name of your choice but extension should be .config and should be saved inside folder called .ebextensions

# Location of configuration file
- The .ebextensions folder must be included in the top-level directory of your application source code bundle.
- configuration files can be placed under source control along with the rest of your application code.

```json
// myHealthCheckUrl.config
{
    "option_settings":
        [
            {
                "namespace":"aws:elasticbeanstalk:application",
                "option_name":"My Application health check url",
                "value":"/healthcheck"
            }
        ]
}
```

This .config file configures an application health check url to be used by ELB.
