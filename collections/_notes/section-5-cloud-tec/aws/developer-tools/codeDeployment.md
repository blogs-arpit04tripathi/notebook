---
layout: post
title: CodeDeployment
permalink: /:collection/aws/devtools/codeDeployment
---

![]({{site.cdn}}/aws/dev-theory/code-deploy-approaches.png)

# CodeDeployment Approaches
## In Place
- Known as rolling update.
- Application is stopped on each instance, capacity is reduced during deployment.
- You should configure your ELB to stop sending requests to the instance.
- CodeDeploy installs new version, known as Revision.
- Instance comes back into service and registered with ELB.
- CodeDeploy contiunes to deploy to next instance.

**How to Rollback?**
- No quick fix.
- You will need to redeploy the previous version, time consuming.

## Blue/Green
- Blue represents the current version of our application.
- New instances are provisioned and the new release (Revision) is installed on the new isntances.
- Green is the new release (environment), gets registered with the ELB.
- Traffic is routed away from the Blue environment.
- Once everything works fine, we can terminate the blue environment.

**How to Rollback?**
- Re-register Blue environment.
- Route Traffic back to Blue environment.
- De-register green environment

|In Place | Blue/Green |
|---|---|
|Capacity Reduced during Deployment|No capacity reduction.|
|Lambda is not supported.|Green instances can be created ahead of time.|
|Rolling back involves a re-deploy.|Easy to switch between old and new.|
|Great when deploying the first time.|You pay for 2 environments until you terminate the old one.|
