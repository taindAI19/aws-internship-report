---
title: "Week 9 Worklog"

weight: 1
chapter: false
pre: " <b> 1.9. </b> "
---
---

### Week 9 Objectives:

**Part 1 – Optimize EC2 Costs with Lambda Function**

* Understand the mechanism of automatically turning on/off EC2 to reduce operating costs.
* Create a tag system to identify servers that need to be processed on a schedule.
* Build a Lambda Function to manage Start/Stop EC2 based on tags.
* Create a periodic schedule using EventBridge Scheduler.
* Monitor actual operations via CloudWatch Logs.
* Reclaim all resources after testing is complete.

**Part 2 – Optimize EC2 Costs with Savings Plan**

* Learn about Savings Plan and the principle of discounting based on commitment level.
* Distinguish between Compute Savings Plans and EC2 Instance Savings Plans.
* Understand the USD/hourly commit mechanism and how the estimator calculates it.
* Know the process of purchasing and applying Savings Plan according to AWS standards.
* Practice estimating costs using AWS Pricing Calculator.

---

### Deployment tasks this week

| Day | Detailed tasks | Start | Complete | Source |
| --- | ------------------ | ---------- | ---------- | ------ |
| 2 | **Analyze EC2 optimization model**<br>• Identify waste problems when EC2 runs 24/7 but the usage volume is low.<br>• Describe the flow of activities: User → EventBridge → Lambda → EC2 API.<br>• Identify workloads suitable for automatic Start/Stop mechanism.<br>• Consider the risks and limitations of turning EC2 on/off. | 03/11/2025 | 03/11/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | **Create EC2 Classification Tag**<br>• Set Tag Key: `Schedule`.<br>• Sample Tag Value: `office-hours`, `training-only`, `weekend-shutdown`.<br>• Assign tags to EC2s that need to be automated.<br>• Check with CLI: `describe-instances --filters tag:Schedule=office-hours`. | 04/11/2025 | 04/11/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | **Create IAM Role for Lambda**<br>• Create role: `LambdaEC2ScheduleRole`.<br>• Assign policy: `AmazonEC2FullAccess` (for lab purposes).<br>• Add logging permission: `AWSLambdaBasicExecutionRole`.<br>• Test trust relationship with `lambda.amazonaws.com`. | 05/11/2025 | 05/11/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | **Develop Lambda Start/Stop EC2**<br>• Write Python code (boto3) to StartInstances/StopInstances.<br>• Add logic to filter instances by tag `<Schedule>`.<br>• Log instance ID enabled/disabled.<br>• Test with “Test event”. | 06/11/2025 | 06/11/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | **Integrate EventBridge Scheduler**<br>• Create a rule to turn on EC2 at 08:00 AM.<br>• Create a rule to turn off EC2 at 18:00 PM.<br>• Assign Lambda as target.<br>• View logs in CloudWatch to confirm operation. | 07/11/2025 | 07/11/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 7 | **Test & Cleanup**<br>• Verify EC2 turns on/off on schedule.<br>• Monitor CloudWatch Logs to handle permission errors.<br>• Delete rules, Lambda Functions and IAM Roles after completion.<br>• Compare EC2 costs before and after optimization. | 08/11/2025 | 08/11/2025 | <https://cloudjourney.awsstudygroup.com/> |

---

### Results achieved in week 9

**1. Optimize EC2 costs via Lambda**

* Successfully set up EC2 on/off process based on working hours.
* Understand how to use Tags to optimize EC2 groups.
* Write Lambda Function to control Start/Stop using boto3.
* Fully automate via EventBridge Scheduler.
* Record full logs: time, instance ID, permission errors.
* Save 50–70% of costs for workloads that do not run continuously.

---

**2. Optimize costs with Savings Plan**

* Understand the discount mechanism of Savings Plan based on USD/hour commitment.
* Use Pricing Calculator to estimate appropriate commitment level.
* Understand the difference between two types of Savings Plan:

* **Compute Savings Plan** – flexible, multi-service application.

* **EC2 Instance Savings Plan** – high savings but with more constraints.
* Understand the process of registering and activating Savings Plan.
* See clearly the savings benefits that can reach ~66%.

---

### Summary of knowledge gained

**AWS Lambda + EC2 Automation**

* Automatically turn on/off EC2 using Lambda.
* Use Boto3 to interact with EC2 API.
* Use EventBridge Scheduler to schedule runs.
* CloudWatch Logs to check and handle errors.

**AWS Savings Plans**

* Cost commitment mechanism to reduce infrastructure usage prices.
* Suitable for workloads running continuously 24/7.
* Classify Compute and EC2 Plans.
* Combine Savings Plan + Auto Scheduling to optimize overall costs.

---