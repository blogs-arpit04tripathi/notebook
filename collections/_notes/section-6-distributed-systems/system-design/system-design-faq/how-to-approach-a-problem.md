---
layout: post
title: Steps To Approach A System Design Problem
permalink: /:collection/system-design/how-to-approach-a-problem
---

# Step 1 - Feature expectations ( First 2 mins ) : 
As said earlier, there is no wrong design. There are just good and bad designs and the same solution can be a good design for one use case and a bad design for the other. It is extremely important hence to get a very clear understanding of whats the requirement for the question.

# Step 2 - Estimations ( 2-5 mins ) 
Next step is usually to estimate the scale required for the system. The goal of this step is to understand the level of sharding required ( if any ) and to zero down on the design goals for the system.

For example,  
- if the total data required for the system fits on a single machine, we might not need to go into sharding and the complications that go with a distributed system design.  , OR 
- if the most frequently used data fits on a single machine, in which case caching could be done on a single machine.

# Step 3 - Design Goals ( 1 mins ) 
Figure out what are the most important goals for the system. It is possible that there are systems which are latency systems in which case a solution that does not account for it, might lead to bad design.

# Step 4 - Skeleton of the design ( 4 - 5 mins ) 
30-40 mins is not enough time to discuss every single component in detail. As such, a good strategy is to discuss a very high level with the interviewer and go into a deep dive of components as enquired by the interviewer.

# Step 5 - Deep dive ( 20-30 mins ) 
This is an extension of the previous section.
