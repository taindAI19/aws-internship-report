---
title: "Blog 2"
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---

# Automating Data Processing with Amazon EMR: Orchestration with Step Functions & EventBridge

As data pipelines continue to grow, the need to **automate processes**, **reduce manual effort**, and **optimize compute costs** is more important than ever. **Amazon EMR** provides a powerful environment for running workloads such as **Apache Spark**, ETL, batch analytics, and data enrichment. However, in many cases – especially in industries that require tight infrastructure control such as finance, healthcare, and government – ​​running transient EMR clusters without automation is costly and operationally risky.

In this blog, I share how to build a **fully automated Spark pipeline** using **EMR on EC2**, orchestrated by **AWS Step Functions** and triggered by **Amazon EventBridge**. This architecture illustrates how to run data processing jobs on a scheduled, cost-effective, and easy-to-administer schedule.

---

## Architecture Guide

The solution uses the public COVID-19 dataset to simulate a periodic data processing pipeline. The entire workflow is separated into independent, replaceable, and scalable components.

The data processing flow consists of 7 main steps:

1. CSV data is stored in S3 (raw input).

2. EventBridge triggers on a schedule, triggering the state machine.

3. Step Functions creates a temporary EMR cluster on EC2.

4. PySpark job is submitted to calculate COVID-19 indicators by state.

5. Results are written to S3 output.
6. EMR cluster automatically deletes after job completion.

7. All logs are saved to S3 for monitoring & troubleshooting.

> This architecture is especially suitable for batch Spark workloads, which require detailed control of the infrastructure but still want to optimize costs.

---

## Automation architecture features

When working with transient EMR clusters, three important factors are considered:

- **Internal**: Spark cluster performance, resource control, EC2 cost optimization
- **External**: scheduled triggers, orchestration of multiple job pipelines
- **Human**: reduce operational burden, limit manual errors, clear audit

The orchestration model using Step Functions helps to clearly monitor the lifecycle – from provisioning → spark submit → cleanup.

---

## Technology selection and communication scope

| Components | Technology used |
| ---------------------------------- | --------------------------------------------------------------------------------- |
| Provision & teardown cluster | AWS Step Functions, Amazon EC2, Amazon EMR |
| Scheduling | Amazon EventBridge Scheduler |
| Data storage & logs | Amazon S3 |
| Observability | Amazon CloudWatch, S3 logs, EMR Application UIs |
| IaC (infrastructure deployment) | AWS CloudFormation |

---

## The orchestration pipeline

A model connecting micro-components is built in an **event-driven** direction:

- EventBridge: triggers workflow.

- Step Functions: manages sequential steps.

- EMR: executes Spark workload.

- S3: stores input, output, and logs.

Advantages of this model:
- Separate compute (EMR) and coordination logic (Step Functions)
- Pay for compute only when the cluster is running
- Transparent processing per state

Disadvantages: need to closely monitor state machine & error handling.

---

## Core workflow components

### 1. Provisioning EMR cluster
Step Functions initializes EMR cluster on EC2 with optimal configuration for workload. IAM roles are set according to **least privilege** principle.

### 2. Spark job execution
The PySpark job is uploaded to S3, and Step Functions sends step submission to EMR cluster.

When run, the script performs:
- Normalize data format
- Remove erroneous records
- Calculate monthly average of:
- inpatient beds
- ICU beds
- COVID-19 patient rate
- Export CSV file by timestamp to S3 output

### 3. Automated teardown
After the job completes, the cluster is automatically deleted to save costs.
No more EC2 costs incurred when forgetting to shut down the cluster.

---

## Setup & operate pipeline

### CloudFormation
A single template deploys the entire infrastructure:
- EMR roles
- S3 buckets
- Log bucket
- Step Functions state machine
- EventBridge schedule

Deployment typically completes in 5 minutes.

### Load and prepare data
Dataset from healthdata.gov is renamed and uploaded to `raw/`.

### PySpark script
The script is uploaded to the `scripts/` directory on S3 and used when submitting the job.

---

## Scheduling with EventBridge

Workflows can run:

- Once
- Periodically (cron or rate-based)
- Business triggers

This turns the Spark pipeline into a recurring ETL system, for example:

- end-of-day report processing
- weekly data aggregation
- periodic health index calculation

---

## Monitoring & observability

### Step Functions monitoring
- Track each state
- Quickly catch errors, view input/output
- Intuitive operation

### EMR monitoring
- Spark step monitoring
- View job details via Spark UI, YARN Timeline
- Observe cluster-level metrics

### CloudWatch logs
If logging is enabled:
- driver logs
- executor logs
- system metrics

All streamed in real time.

> Multi-layer observation helps shorten troubleshooting time, especially with complex Spark workloads.

---

## Processing & Testing Results

The CSV output is saved to the
s3://<output-bucket>/processed/<timestamp>/

The output can be used for:

- dashboard analytics

- compliance reporting
- downstream data enrichment

---

## Resource Cleanup

To avoid additional costs:

- Delete S3 buckets (input/output/log)
- Delete CloudFormation stack
- Recheck EventBridge schedule to avoid unwanted triggers

---

## Conclusion

The solution using **Amazon EMR + Step Functions + EventBridge** provides a **fully automated**, **cost-effective**, and **observable** approach to Spark on-demand processing.

This is an ideal choice for businesses that want to:
- Automate ETL/batch analytics pipeline
- Reduce compute costs with temporary clustering
- Maintain granular control over security and infrastructure
- Ensure enterprise-standard auditing, logging, and scheduling

You can extend this solution by:
- adding more Spark jobs
- adding more complex workflows in Step Functions
- integrating partitioned output with Glue Data Catalog
- integrating with Lake Formation for data control

---