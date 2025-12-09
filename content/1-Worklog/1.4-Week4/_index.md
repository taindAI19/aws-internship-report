---
title: "Week 4 Worklog"
weight: 1
chapter: false
pre: " <b> 1.4. </b> "
---

### Week 4 Objectives:

* Master how to **securely grant access to AWS resources** to applications.

* Clearly distinguish between the operating mechanism between **Access Key/Secret Access Key** and **IAM Role**.
* Know the process of **creating and assigning IAM Roles to EC2 Instances**, allowing applications to access AWS services without having to include authentication information in the source code.
* Get familiar with the browser-based development environment **AWS Cloud9**, which has built-in AWS CLI.
* Practice **writing code, testing, debugging** and managing source code directly on Cloud9.

---

### Deployment tasks of the week

| Day | Task | Start date | Completion date | Document source |
| --- | --------- | ------------- | ---------------- | --------------- |
| 2 | - Overview of **IAM** and AWS access control mechanism <br> - Review the concepts of **User**, **Group**, **Policy**, **Role** <br> - Learn how AWS authenticates & authorizes access | 09/22/2025 | 09/22/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | - Testing authorization using **Access Key/Secret Access Key** <br> - Testing AWS access applications using Access Key <br> - Analyzing risks and vulnerabilities when embedding Access Key in applications | 09/23/2025 | 09/23/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Create **IAM Role for EC2** <br> - Assign role to instance and check S3/DynamoDB access via Node.js sample application <br> - Retest application after revoking permission | 09/24/2025 | 09/24/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Initialize and get familiar with **Cloud9 IDE** <br> - Set up workspace, configure working environment <br> - Experience terminal, file explorer, debugger, syntax highlight | 09/25/2025 | 09/25/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - **Summary exercises:** <br>&emsp; + Write scripts to operate AWS CLI in Cloud9 <br>&emsp; + Build a Node.js CRUD (User Management) application running directly on Cloud9 <br>&emsp; + Delete resources to avoid charges | 09/26/2025 | 09/26/2025 | <https://cloudjourney.awsstudygroup.com/> |

---

### Results achieved in week 4

* Understand the difference between **IAM Role** and **Access Key**, as well as why using roles is a safer choice in practice.
* Know how to create **IAM Role** with appropriate permissions, such as read/write access to S3.
* Assign IAM Role to EC2 Instance and allow applications running on it to access AWS services without fixed credentials.
* Proficiently use **AWS Cloud9** to:

* Create a development workspace.
* Connect to EC2.
* Run AWS CLI commands, write and test code directly.
* Deploy a small Node.js application connecting to S3 or DynamoDB directly in Cloud9.
* Understand the process of **reclaiming, deleting resources** after the exercise to optimize costs.

---

### Summary of accumulated knowledge

- **IAM Role:** Dynamic authorization mechanism, reducing security risks due to no need to use Access Key.
- **Access Key:** Understand the weaknesses when using directly in code or on the developer machine.
- **AWS Cloud9:** A flexible programming environment on the browser, supporting many languages ​​and integrating AWS CLI.
- **AWS CLI/SDK:** Tools to access and manipulate AWS services based on IAM Role.
- **Actual deployment process:** Set up the environment, write and run the application, check access rights, and clean up resources when finished.

---