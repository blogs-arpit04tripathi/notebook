---
layout: post
title: Beanstalks Deployment Policies
permalink: /:collection/aws/beanstalks/deployment-policies
---

- TOC
{:toc}

<hr><br>

# All at Once
- Deploys the new version to all instances simultaneously.
- All of your instance are out of service while the deployment takes place.
- You will experience an outage while the deployment is taking place - not ideal for mission critical production system.
- If the update fails, you need to roll back the changes by re-deploying the original version to all your instances.

# Rolling Deployment
- Deploys the new version in batches.
- Each batch of instances is taken out of service while deployment takes place.
- Your environment capacity would be reduced by no. of instances in the batch.
- Not ideal for performance sensitive systems.
- If update fails, you need to perform an additional rolling update to roll back the changes.

# Rolling with additional batch
- Launches additional batch of instances.
- Deploys the new version in batches.
- Maintains full capacity during the deployment process.
- If the update fails, you need to perform an additional rolling update to roll back the changes.

# Immutable
- Deploys new version to fresh group of instances in their own new autoscaling groups.
- When the new instances pass their health checks, they are moved to your existing auto-scaling group and finally old instances are terminated.
- Maintains full capacity during deployment process.
- Impact of failed update is far less, and rollback process only requires terminating the new autoscaling group.
- Preferred option for mission-critical production systems.
