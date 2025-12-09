---
title: "Week 7 Worklog"
weight: 1
chapter: false
pre: " <b> 1.7. </b> "
---

---

### Week 7 Objectives:

**Part 1 – AWS CloudWatch**

* Build a clear understanding of how CloudWatch is structured and how each component functions, including Metrics, Logs, Events, Dashboards, and Alarms.  
* Observe and analyze service-level metrics from EC2, RDS, and Lambda in an actual AWS environment.  
* Configure log collection and learn how CloudWatch Logs stores, indexes, searches, and processes application and system logs.  
* Create and refine alert thresholds to support continuous operational monitoring.  
* Design dashboards that visualize system health and performance in real time.  
* Use Container Insights to evaluate the behavior and performance of containerized workloads.  
* Remove unused monitoring components to optimize overall cost.

**Part 2 – Hybrid DNS with Route 53 Resolver**

* Understand the architectural mindset behind linking on-premises DNS with AWS.  
* Create inbound and outbound Route 53 Resolver endpoints.  
* Build Resolver Rules to forward DNS queries to the appropriate domain.  
* Integrate an internal Active Directory DNS server with a Route 53 Private Hosted Zone.  
* Test two-way name resolution between AWS and on-premises environments.  
* Clean up all created resources when the implementation is complete.

---

### Tasks Completed During the Week

| Day | Detailed Work | Start Date | Completion Date | Reference |
| --- | ------------- | ---------- | ---------------- | ---------- |
| 2 | **CloudWatch – Overview & Architecture** <br> • Study CloudWatch’s design goals and how it integrates with AWS services. <br> • Explore in detail how Metrics, Logs, Alarms, Events, Dashboards, and Container Insights operate. <br> • Compare basic monitoring with detailed monitoring. <br> • Review the end-to-end workflow: application → log agent → log groups → metrics → alarm → SNS → automated action. <br> • Create the first chart from EC2 data. | 20/10/2025 | 20/10/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | **CloudWatch Metrics & Logs – Practical Setup** <br> • Create a Log Group and learn how Log Streams are managed. <br> • Install the CloudWatch Agent to gather OS-level data such as CPU, memory, and network usage. <br> • Modify the `cloudwatch-agent.json` configuration to collect system logs and application logs. <br> • Build metric filters to identify recurring error patterns (“ERROR”, “Failed”, “CRITICAL”). <br> • Push custom metric data manually using AWS CLI. <br> • Adjust retention periods and examine their impact. | 21/10/2025 | 21/10/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | **CloudWatch Alarms & Dashboards – Automating Alerts** <br> • Configure a CPU alarm triggered when usage exceeds 70% for 5 minutes. <br> • Create an EC2 Status Check alarm to track instance health. <br> • Connect alarms to SNS topics for email notifications. <br> • Use alarms to perform automated actions, such as rebooting an EC2 instance. <br> • Build dashboards containing multiple widget types for logs, metrics, and system states. <br> • Create a consolidated dashboard showing EC2, RDS, and network metrics. <br> • Enable Container Insights to analyze CPU/memory usage and container restarts. | 22/10/2025 | 22/10/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | **Route 53 Resolver – Understanding Hybrid DNS Architecture** <br> • Review Private Hosted Zones and the DNS resolution flow inside a VPC. <br> • Create an Outbound Resolver Endpoint to forward DNS queries from AWS to on-premises. <br> • Create an Inbound Resolver Endpoint to receive DNS queries from on-premises. <br> • Add a forwarding rule for the domain “corp.local” to the internal AD DNS server. <br> • Validate endpoints and associate rules with the VPC. | 23/10/2025 | 23/10/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | **Microsoft AD + DNS Integration – Simulating On-Premises DNS** <br> • Deploy a Windows Server EC2 instance and install Active Directory Domain Services. <br> • Create the domain “corp.local” along with its DNS zone. <br> • Configure a Conditional Forwarder pointing to AWS’s Inbound Endpoint. <br> • Add A and CNAME records inside the internal DNS. <br> • Test bi-directional name resolution: <br>   – From AWS: `nslookup dc1.corp.local` <br>   – From AD: `nslookup api.internal.aws` <br> • Simulate endpoint failure and observe fallback behavior. | 24/10/2025 | 24/10/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 7 | **Resource Cleanup and Cost Optimization** <br> • Remove unused Log Groups, Log Streams, Dashboards, and Alarms. <br> • Disable Container Insights to prevent additional charges. <br> • Delete Route 53 Resolver Endpoints. <br> • Remove all Resolver Rules. <br> • Shut down the AD domain controller. <br> • Terminate all test EC2 instances. <br> • Review the billing breakdown for CloudWatch Logs, metrics, and endpoint costs. | 25/10/2025 | 25/10/2025 | <https://cloudjourney.awsstudygroup.com/> |

---

### Outcomes Achieved in Week 7

#### 1. AWS CloudWatch

**CloudWatch Metrics – Collection & Analysis**  
* Identified the default metrics provided by EC2, EBS, VPC, and Load Balancers.  
* Created custom metrics via AWS CLI to validate ingestion pipelines.  
* Examined long-term data storage and high-resolution metrics.  
* Detected anomalies such as CPU spikes, sudden network surges, and abnormal Disk I/O activity.

---

**CloudWatch Logs – Application and System Log Monitoring**  
* Installed agents to send OS and application logs to CloudWatch.  
* Created log groups and log streams for monitoring and debugging.  
* Configured log retention and tested exports to S3 for long-term archiving.  
* Identified common issues such as unauthorized access, throttling, and CPU credit depletion.

---

**CloudWatch Alarms – Notification & Recovery**  
* Built threshold-based alarms for continuous EC2 monitoring.  
* Created system-check alarms to ensure host stability.  
* Configured SNS notifications for incident alerts.  
* Enabled automatic recovery actions for hardware-level failures.

---

**CloudWatch Dashboards – Real-Time Visibility**  
* Constructed real-time dashboards for system observability.  
* Added data from EC2, NAT Gateway, RDS, and ELB into unified views.  
* Organized metrics using multiple widget types for clear visualization.

---

**Container Insights – Observing Microservices**  
* Enabled monitoring for ECS and Fargate workloads.  
* Visualized container-level CPU/memory usage.  
* Used restart counts to identify potential application issues.  
* Evaluated how Container Insights accelerates troubleshooting.

---

**Resource Cleanup**  
* Removed unused dashboards, alarms, and custom metrics.  
* Uninstalled CloudWatch Agents where unnecessary.  
* Deleted log groups and turned off Container Insights.  

---

**Summary of Achievements**  
* Gained a full understanding of the monitoring pipeline from data collection to automated remediation.  
* Successfully implemented the workflow: **metrics → logs → alarms → dashboards**.  
* Improved the ability to diagnose issues using CloudWatch data.  
* Enhanced operational efficiency and cost control.  
* Built a real-time monitoring and alerting flow suitable for DevOps/SRE work.

---

#### 2. Hybrid DNS Deployment with Route 53 Resolver

**Understanding Hybrid DNS Architecture**  
* Identified common challenges when integrating on-premises DNS with cloud environments.  
* Reviewed how inbound/outbound endpoints and Resolver Rules work together.

---

**Environment Preparation**  
* Created a dedicated VPC and private subnets for DNS endpoints.  
* Configured Security Groups to allow DNS traffic on port 53.  
* Deployed a Windows Server to simulate an on-premises Active Directory environment.

---

**Remote Access via RDGW**  
* Used an RDGW instance to access private subnets.  
* Validated DNS resolution inside the VPC before hybrid integration.

---

**Microsoft Active Directory Setup**  
* Built a domain controller to simulate local infrastructure.  
* Configured a DNS zone such as `company.local`.  
* Validated SRV, A, and NS records.

---

**Hybrid DNS Configuration**

**Outbound Endpoint**  
* Allowed AWS to forward internal DNS queries to the on-premises AD server.  
* Attached Resolver Rules to route internal domains.

**Inbound Endpoint**  
* Accepted DNS queries from on-premises AD to AWS’s Private Hosted Zone.  
* Verified that AWS-based private records were resolving properly.

**Resolver Rules**  
* Created forwarding rules for internal domains.  
* Used system rules for default VPC DNS behavior.

---

**Full End-to-End DNS Testing**  
* Verified name resolution from AD → AWS and AWS → AD.  
* Compared latency and reliability in both directions.  
* Ensured that all DNS records resolved accurately.

---

**Cleanup Activities**  
* Removed endpoints and Resolver Rules.  
* Deleted Private Hosted Zones and test DNS records.  
* Shut down AD servers and test EC2 instances.

---

### Knowledge Summary

**CloudWatch:**  
* End-to-end monitoring for logs and metrics.  
* Automated alerting and response.  
* Effective dashboarding for system visibility.  
* Integrated monitoring for containerized workloads.

**Route 53 Hybrid DNS:**  
* Clear understanding of hybrid DNS principles.  
* Successful integration of on-premises DNS with AWS.  
* Fully functioning two-way name resolution.  
* Readiness to apply DNS design in enterprise hybrid environments.
