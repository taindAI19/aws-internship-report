---
title: "Week 5 Worklog"
weight: 1
chapter: false
pre: " <b> 1.5. </b> "
---

### Week 5 objectives:

* Master the working mechanism of **Amazon S3**, understand the object storage structure, storage options and the scope of application in practice.

* Deploy **static website** on S3: enable hosting features, fine-tune access rights and test the speed of operation.

* Master the **security settings for bucket**, including blocking public access, writing IAM policies and configuring Bucket Policy securely.

* Get familiar with advanced operations: **Versioning**, **Transfer Acceleration**, **Replication to another region**, and object migration commands.

* Perform the **resource release** process correctly to avoid unexpected costs and comply with best practices when using S3.

---

### Tasks to be implemented this week:

| Day | Task | Start date | Completion date | Resources |
| --- | ---------- | ------------- | ---------------- | --------------- |
| 2 | **Background review & environment preparation** <br>&emsp; + Explain the concepts of bucket, object, region, key and storage classes (STANDARD, IA, GLACIER) <br>&emsp; + Understand durability levels (11-nines) and availability <br>&emsp; + Summarize suitable problems for S3: static website, backup, data analysis | 06/10/2025 | 06/10/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | **Initialize bucket & enable website hosting** <br>&emsp; + Create bucket according to the naming rules and select region <br>&emsp; + Upload `index.html`, `error.html` <br>&emsp; + Enable Static Website Hosting mode and access the endpoint to test | 07/10/2025 | 07/10/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | **Set up Public Access & configure Bucket Policy** <br>&emsp; + Understand Block Public Access modes at the account and bucket levels <br>&emsp; + Write Bucket Policy to only allow public a specific object (index.html) <br>&emsp; + Check website access via browser <br>&emsp; + Try to revoke public access and recheck security behavior | 08/10/2025 | 08/10/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | **Improve speed & expand hosting capabilities** <br>&emsp; + Compare advantages — limitations between: S3 + CloudFront, S3 Transfer Acceleration, AWS Amplify Hosting <br>&emsp; + Enable Transfer Acceleration and benchmark speed with `curl` in multiple locations <br>&emsp; + (Optional) Create a CloudFront to enable HTTPS/CDN <br>&emsp; + Add CloudWatch monitoring and evaluate usage costs | 09/10/2025 | 09/10/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | **Lifecycle management, replication & resource cleanup** <br>&emsp; + Enable Versioning to control object changes and try to restore old files <br>&emsp; + Set Lifecycle to switch to IA/Glacier after a certain number of days <br>&emsp; + Set up Cross-Region Replication with corresponding IAM Role <br>&emsp; + Use cp/mv/sync to transfer data between bucket/region <br>&emsp; + Delete test resources: disable acceleration, remove CloudFront, empty bucket, delete bucket | 10/10/2025 | 10/10/2025 | <https://cloudjourney.awsstudygroup.com/> |

---

### Results achieved in week 5:

**1. Basic setup & operation:**
- Complete AWS CLI configuration (Access Key, Secret Key, Region).

- Check CLI status with:
- `aws configure list`
- `aws s3 ls` (list buckets)
- `aws s3api list-buckets` (see details)
- Create/Delete bucket with command:
- `aws s3 mb s3://bucket-ten`
- `aws s3 rb s3://bucket-ten --force`

**2. Static Website Hosting:**
- Create a new bucket, put HTML file in and enable hosting.
- See website running through provided endpoint.
- Check error page when accessing non-existent file to ensure error.html works properly.

**3. Manage permissions & security:**
- Try enabling/disabling Block Public Access to observe the difference.
- Write a bucket policy to publicize only one file.
- Test access rights by public/private each object.

**4. Data Management & Performance Acceleration:**
- Enable versioning and try uploading multiple versions of the same file.

- Restore files from older versions to understand the mechanism.

- Apply lifecycle rules to automatically move objects to IA or Glacier.

- Test Transfer Acceleration speed using curl from multiple regions.

**5. Replication & Data Migration:**
- Set up CRR and observe objects being replicated to other regions.

- Use commands:
- `aws s3 cp`
- `aws s3 mv`
- `aws s3 sync`
- Check the destination bucket to verify successful replication.

**6. Cleanup & Optimize Usage Costs:**
- Delete test objects, disable Transfer Acceleration and CloudFront.
- Delete test bucket, turn off hosting.
- Summary of best practices to help control costs and ensure data security.

---

### Notes:

- Always avoid publicizing the entire bucket — only public objects that are absolutely necessary.

- Block Public Access is an important security layer, only override if you understand the rights and risks.

- Versioning combined with Lifecycle helps manage data long-term while still saving costs.
- CloudFront suitable when HTTPS, private domain and global performance are needed; Transfer Acceleration is suitable when clients often upload remotely.
- Amplify Hosting is a simple choice when only needing to deploy static websites from Git repo.
- IAM must be tightly configured, do not save Access Key in source code.
- CloudWatch + S3 Storage Lens supports monitoring capacity, traffic and costs.
- When deleting buckets with Versioning, it is necessary to delete all versions + delete markers, to avoid unwanted storage charges.

---

### Summary of knowledge gained:

- Operate S3 at full level: hosting, security, replication, versioning and cost optimization.
- Know how to choose the right static site deployment solution: pure S3, S3 + CloudFront, or Amplify.
- Effectively use big data management tools: lifecycle, policy, replication, sync/copy.
- Understand the resource cleaning process to avoid incurring costs.

---