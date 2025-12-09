---
title: "Week 6 Worklog"

weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---

---

### Week 6 Goals:

* Get familiar with the method of **monitoring, analyzing performance** through Performance Insights, Monitoring and Enhanced Logging.
* Understand the overall architecture of **Amazon RDS**, including engines such as MySQL, PostgreSQL, MariaDB, SQL Server…
* Practice **backup – restore – snapshot – automated backup – failover** to ensure data recovery.
* Create, configure and operate an **RDS Instance** from foundation to advanced configuration.
* Build **parameter group**, **subnet group**, **security group** specifically for RDS.
* Set up connections between RDS and environments such as **EC2**, **Cloud9**, or local machines.

* Master the **resource scaling** and **cost optimization** methods, and know how to clean up resources when no longer needed.

---

### Tasks to be deployed this week:

| Day | Task | Start date | Completion date | Document source |
| --- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | -------------- |
| 2 | **RDS Introduction** <br>  + Engine options <br>  + Multi-AZ and Read Replica models <br>  + Backup & snapshot cycles | 13/10/2025 | 13/10/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | **Initialize RDS Instance** <br>  + Build Subnet Group <br>  + Configure Security Group for Cloud9/EC2 <br>  + Choose engine, capacity and instance type | 10/14/2025 | 10/14/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | **Connect & operate on RDS** <br>  + Access from EC2 or Cloud9 <br>  + Create schema & data table <br>  + CRUD actions using MySQL or PostgreSQL client | 10/15/2025 | 10/15/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | **Monitoring – Backup – Restore** <br>  + Create manual snapshot <br>  + Restore instance from snapshot <br>  + Check CPU, connection, throughput <br>  + Use Performance Insights to analyze queries | 10/16/2025 | 10/16/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | **Scaling – Optimizing – Reclaiming resources** <br>  + Increase/decrease instance class <br>  + Expand storage capacity <br>  + Adjust backup retention appropriately <br>  + Delete unused snapshots & RDS | 10/17/2025 | 10/17/2025 | <https://cloudjourney.awsstudygroup.com/> |

---

### Results achieved in week 6:

**1. Master the Backup – Restore – Snapshot process:**
* Create a manual snapshot.
* Restore to a new RDS instance.
* Observe the backup window.
* Confirm that automated backups are automatically created every day.

**2. Understand the operating mechanism of Amazon RDS:**
* Recognize the difference between Single-AZ, Multi-AZ and Read Replica.
* Understand how automated backups work and how long they are stored.
* Understand that snapshots are manual archives and are not automatically deleted.

**3. Connect to RDS from local/EC2/Cloud9:**
* Install MySQL/PostgreSQL client to access.
* Connect using endpoint: mysql -h endpoint.amazonaws.com -u admin -p
* Create database, table and execute CRUD commands:
* `CREATE DATABASE demo;`
* `CREATE TABLE users (...);`
* `INSERT`, `SELECT`, `UPDATE`, `DELETE`

**4. Configure a complete RDS Instance:**
* Create DB Subnet Group including 2 subnets in two different AZs.
* Create Security Group to allow connection (port 3306/5432).
* Install:
* Engine MySQL/PostgreSQL
* Instance class db.t3.micro
* Storage gp3 20GB
* Backup retention
* Endpoint private or public

**5. Monitor system performance & activity:**
* Monitor CPU, RAM, number of connections via Monitoring.
* Use Performance Insights to find queries that cause heavy load.
* Check Slow Query Log when enabled.

**6. Optimize costs and scale resources:**
* Change instance class t3.micro → t3.small according to load demand.
* Increase storage capacity to 30GB when needed.
* Adjust backup retention time to 3 days to save costs.
* Delete snapshots that no longer serve storage purposes.

**7. Clean up resources:**
* Delete RDS instance.
* Delete subnet group and corresponding security group.
* Clean up all old snapshots.

---

### Summary of knowledge gained

* Understand the working mechanism of Amazon RDS and popular engines.
* Create, operate and connect to RDS from Cloud9, EC2 or local machine.
* Understand the backup platform, snapshot and recovery process.
* Know how to use Performance Insights to evaluate query performance.
* Get familiar with using cale resources and optimize costs.
* Practice resource cleaning to avoid additional costs.

---