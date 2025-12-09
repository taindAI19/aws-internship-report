---
title: "Week 3 Worklog"
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---

### Week 3 Objectives:

* Understand the concept and purpose of using **Amazon EC2 (Elastic Compute Cloud)**.
* Become familiar with the process of **initializing, accessing, configuring and managing EC2 virtual machines** on Windows and Linux environments.
* Conduct a trial deployment of a **basic web application (AWS User Management)** onto EC2 instances.
* Practice skills in **monitoring, securing and optimizing EC2 resources** throughout the usage process.

---

### Tasks to be deployed this week:

| Day | Task | Start date | Completion date | Document source |
| --- | ---------- | ------------- | ---------------- | --------------- |
| 2 | - Get an overview of **Amazon EC2** and important terms: <br>&emsp; + Instance, AMI, Key Pair, Elastic IP, Security Group, Volume <br>&emsp; + Cost models: On-Demand, Spot, Reserved Instance, Savings Plan | 09/22/2025 | 09/22/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | - **Practice:** Create and set up **Windows EC2 instance** <br>&emsp; + Choose the appropriate AMI and instance type <br>&emsp; + Create a key pair, adjust the security group <br>&emsp; + Connect via Remote Desktop (RDP) <br>&emsp; + Explore the Windows Server 2022 interface | 09/23/2025 | 09/23/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - **Practice:** Initialize and set up **Linux EC2 instance** <br>&emsp; + Create Amazon Linux 2 virtual machine <br>&emsp; + Log in using SSH with key pair <br>&emsp; + Get familiar with terminal and basic commands <br>&emsp; + Update packages and system | 09/24/2025 | 09/24/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - **Deploy “AWS User Management” application** <br>&emsp; + Install Node.js, npm and necessary dependencies on Windows & Linux <br>&emsp; + Deploy CRUD application to manage users <br>&emsp; + Test add, edit, delete, search functions <br>&emsp; + Allow others to access the application via Security Group | 09/25/2025 | 09/25/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - Learn about EC2 monitoring and management tools: <br>&emsp; + Amazon CloudWatch (monitor metrics & logs) <br>&emsp; + AWS Systems Manager <br>&emsp; + EC2 Instance Connect <br> - Collect and release resources: delete unused instances, Elastic IPs, Security Groups | 09/26/2025 | 09/26/2025 | <https://cloudjourney.awsstudygroup.com/> |

---

### Results achieved in week 3:

* Understand **important components of Amazon EC2**, including:

* **AMI:** Operating system template and software to create instances.
* **Instance Type:** Performance regulation (CPU, RAM, storage).
* **Key Pair:** Secure login authentication tool.

* **Elastic IP:** Static IP address for public access.
* **Security Group:** Protection layer to control access flow.

* Successfully created and configured **both Windows and Linux EC2 instance**:
* Connected using **RDP (Windows)** and **SSH (Linux)**.
* Controlled the instance via **AWS Console and CLI**.
* Adjusted **network rules (ports 80, 443, 22, 3389)** to serve the web application.

* Completed deployment of **AWS User Management** application on two operating systems:
* Installed runtime environments such as **Node.js** and **npm**.
* Fully operational CRUD functionality.
* Allowed others to access via **Public IP or Elastic IP**.

* Successfully apply **instance monitoring** methods:
* Use **CloudWatch** to monitor resources (CPU, RAM, network).
* Use **Systems Manager** to automate and manage sessions.
* Take advantage of **EC2 Instance Connect** for quick access via browser.

* Improve the ability to **manage EC2 costs and resources**:
* Turn off or delete instances that are no longer needed.
* Reclaim redundant Elastic IPs.
* Clean up unnecessary Security Groups and Key Pairs.

---

### Summary of knowledge gained:

- **Amazon EC2:** Understand the operating mechanism and how to deploy virtual servers in a cloud environment.
- **Windows & Linux administration:** Understand how to access, configure and secure on the two operating systems.
- **Application deployment:** Complete deployment of Node.js CRUD application on EC2.
- **System Monitoring:** Know how to use CloudWatch & Systems Manager to monitor performance.

- **Cost Optimization:** Ability to analyze and clean up resources to reduce operating costs.

---