---
title: "Week 8 Worklog"
weight: 1
chapter: false
pre: " <b> 1.8. </b> "
---

### Week 8 Objectives:

This week focuses on two groups of content: NoSQL storage with DynamoDB and high-speed caching with Redis in ElastiCache. The main goal is to understand how these two services operate, their data structures, scalability, and how to combine them to speed up read operations in the system.

---

## Part 1 – Amazon DynamoDB

* Survey of key-value and document data models, characteristics of DynamoDB.
* Understand the partitioning mechanism, how to choose keys to avoid hotspots.
* Delve into important concepts: RCU/WCU, On-Demand mode, TTL, Streams, and Global Tables.
* Design tables with Partition Key and Sort Key; Try configuring GSI and LSI for different query types.
* Get familiar with CRUD operations and advanced queries via Query/Scan, combining FilterExpression and ConditionExpression.
* Use AWS CLI and JSON files to interact with tables.
* Import test data to evaluate query performance.

---

## Part 2 – Amazon ElastiCache for Redis

* Review the principles of in-memory caching and how Redis organizes clusters (cluster mode enabled/disabled).
* Create a Redis environment: configure nodes, subnet groups, security groups, and parameter groups.
* Connect from EC2 via redis-cli to test operations.
* Try basic commands: SET/GET, TTL, EXPIRE, and RDB snapshots.
* Apply the Cache-Aside model to combine Redis with DynamoDB.
* Compare latency between cache queries and DynamoDB queries.
* Reclaim resources after completion.

---

### Tasks

| Day | Implementation Content | Start | Finish | Documentation |
| --- | ------------------- | ------- | ---------- | -------- |
| 2 | **DynamoDB Overview** <br> Explore NoSQL structure, partitioning mechanism, throughput, and components such as GSI/LSI, TTL, Streams. Understand how DynamoDB distributes data by Partition Key and the impact of key selection on performance. | 2025-10-27 | 2025-10-27 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | **Table & Query Design** <br> Create tables with partition keys and sort keys; add GSI to extend query paths. Test TTL mechanism, perform enough CRUD and compare Query/Scan in real-world scenarios. | 2025/10/28 | 2025/11/28 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | **Working with CLI** <br> Initialize tables using CLI, import sample JSON data, run queries using KeyConditionExpression, conditionally update, and monitor throughput consumption. | 2025/10/29 | 2025/10/29 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | **Redis – Architecture and Deployment** <br> Prepare subnet group, security group, create Redis cluster with primary and replica, enable failover, then test connection from EC2. | 2025/10/30 | 2025/10/30 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | **DynamoDB – Redis Integration** <br> Test redis-cli with GET/SET/TTL, try snapshots, set Cache-Aside (cache hit/miss) and measure latency between Redis and DynamoDB. | 2025/10/31 | 2025/10/31 | <https://cloudjourney.awsstudygroup.com/> |
| 7 | **Cleanup and Evaluation** <br> Delete Redis Cluster and related groups; remove test DynamoDB table. Check billing to determine cost incurred and note speed difference between cache and database. | 2025/11/11 | 2025/11/11 | <https://cloudjourney.awsstudygroup.com/> |

---

### Results in Week 8

#### 1. DynamoDB

**Data Design & Modeling**

* Understand how DynamoDB distributes data and scales horizontally.

* Practice building appropriate partition/sort keys to reduce partition collisions.

* Experience the role of GSI/LSI secondary indexes in shaping access patterns.

**Query & Update**

* Complete full CRUD via console and CLI interface.
* Proficiently use KeyConditionExpression for conditional queries.

* Know how to combine FilterExpression, UpdateExpression in complex filtering scenarios.
* Survey Scan and its limitations when data is large.

**Advanced Features**

* Enable TTL and observe record removal behavior.

* Try DynamoDB Streams to see how to log changes.

* Evaluate costs based on read/write demand and actual consumption.

---

#### 2. ElastiCache for Redis

**Deploy Redis cluster**

* Build a Redis cluster in VPC with full network configuration.

* Test replication and failover operations.

* Test connection from EC2 to confirm stable operating environment.

**Operations and observations**

* Perform SET, GET, DEL, TTL, EXPIRE in many scenarios.

* Measure the impact of RDB snapshots on data state.

* Evaluate cache behavior when capacity is limited.

---

#### 3. Combine DynamoDB – Redis (Cache-Aside)

* Build a processing flow: check cache → query DynamoDB if missing → return data to Redis.

* Compare cache hit and miss results, measure real latency to derive performance characteristics.
* Recognize why read-intensive systems often use Redis as a cache layer.
* Identify typical use cases: sessions, user profiles, high-frequency lookup data.

---

### Knowledge synthesis

**DynamoDB**

* Distributed NoSQL model.
* How to choose the right Partition Key and Sort Key.

* Common query types and related expressions.
* Throughput mechanism according to RCU/WCU or On-Demand.
* TTL and Streams for data lifecycle management.

**ElastiCache Redis**

* High-speed cache model based on RAM.
* Cluster configuration, replica and failover.
* TTL, snapshot and temporary data processing.

**DynamoDB – Redis integration**

* Apply Cache-Aside to reduce read load.
* Cache hit/miss analysis.
* Performance optimization in large services.

---