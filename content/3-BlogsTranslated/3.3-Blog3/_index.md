---
title: "Blog 3"
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---

# Accelerate Spark Application Development on Amazon EMR
## With Data Solutions Framework (DSF) on AWS

As enterprises increasingly rely on big data processing, developing and operating **Apache Spark** applications requires a unified, repeatable, and maintainable process. However, many engineering teams still face difficulties: heterogeneous Spark configurations, distributed source code, unstandardized pipelines, or unautomated deployment workflows.

To address this issue, AWS introduced **Data Solutions Framework (DSF)** – a standardized development framework that simplifies the process of building, testing, packaging, and deploying Spark applications on **Amazon EMR**. In this blog, I show how DSF accelerates the development lifecycle, standardizes the Spark pipeline, and brings tangible benefits to data engineering teams.

---

## What is DSF?

**Data Solutions Framework on AWS** is a standardized toolkit that allows you to:

- Develop Spark applications in a modular model
- Standardize project structure
- Easily package them for deployment on EMR
- Integrate with services like AWS Glue, EMR, S3
- Support CI/CD pipelines (GitHub Actions, CodePipeline)
- Reduce heterogeneous Spark configuration errors

DSF helps engineering teams avoid the need to build a standard framework for Spark from scratch, while avoiding fragmentation between projects.

---

## Solution Architecture with DSF

DSF defines three main layers:

1. **Framework Layer** – provides abstraction for reading, writing, processing, logging, config.

2. **Application Layer** – where Spark business logic is written (ETL, transform…).

3. **Pipeline & Deployment Layer** – CI/CD, packaging, orchestration and job submission.

General workflow:

- Developer writes Spark jobs according to DSF standard
- DSF CLI is used to run locally, test logic, and package
- Artifact is uploaded to S3
- EMR cluster executes DSF standard jobs via bootstrap or step submit
- Monitoring & logging integrated via CloudWatch and S3

> Strengths: completely separates task code (business logic) from infrastructure (EMR config).

---

## Benefits of using DSF

### 1. Standardize project structure
Spark projects will have a unified layout:
src/
main/
python/
resources/
conf/
tests/
scripts/

This makes onboarding developers easier, reducing confusion between projects.

### 2. Centralized configuration management
DSF supports **YAML-based config**, including:

- input/output paths
- desired Spark settings
- environment-specific overrides

→ No more hardcoded config in Spark code.

### 3. Simple local debugging & running
Through DSF CLI, you can run the pipeline locally – simulating the same as when running on EMR.

### 4. Automatic packaging
DSF automatically packages the application with dependencies → deploy directly to EMR.

### 5. Orchestration support
DSF works well with:

- **AWS Step Functions**
- **Amazon MWAA / Airflow**
- **Amazon EMR on EC2** or **EMR Serverless**

---

## Supported tools: DSF CLI

DSF CLI provides commands:

- `dsf init` – create a standardized Spark project
- `dsf run` – run the application locally/test
- `dsf package` – package & build
- `dsf deploy` – upload artifact to S3
- `dsf generate` – create a config file or module template

> CLI simplifies the workflow: Build → Test → Deploy.

---

## Development process with DSF

Standard process when developing Spark applications with DSF:

### **1. Project initialization**
Developers use DSF CLI to create projects with full modules and standard structures.

### **2. Write Spark processing logic**
ETL or transform logic is separated by module, easy to maintain.

### **3. Set up YAML configuration**
Includes:
- dataset inputs
- schema
- Spark settings
- running environment (dev, staging, prod)

### **4. Run local to unit test**
DSF allows running locally without EMR → accelerate development.

### **5. Build & package**
Artifact contains code + configs that are built automatically.

### **6. Deploy & orchestrate**
Artifact is pushed to S3, then run on EMR via Step Functions/Airflow.

---

## Integration with Amazon EMR

DSF supports many Spark running models:

### **1. EMR on EC2**
- Highly customizable
- Suitable for heavy workloads
- Runs on job flow or step submit model

### **2. EMR Serverless**
- No cluster management required
- Automatic scaling
- Suitable for flexible or ad-hoc workloads

### How DSF makes EMR more efficient:

- Unified configuration → easy to run multiple environments
- Consistent packaging → reduced deployment errors
- Standardized logging → easier debugging
- Easy automation with Step Functions or EventBridge

---

## CI/CD for Spark applications using DSF

Built-in DSF for pipeline:

- **GitHub Actions**
- **AWS CodePipeline + CodeBuild**

Sample pipeline:

1. Developer pushes code
2. CodeBuild runs unit test
3. DSF package application
4. Upload artifact to S3
5. Trigger run on EMR (optional)

→ Easy to ensure quality & consistency when deploying.

---

## Logging & Observability

When running a Spark job with DSF:

- Logs are sent about Amazon CloudWatch

- Detailed driver/executor logs are saved to S3

- Framework supports standardized logging

This makes forensics, auditing, and debugging convenient for data teams.

---

## Extending the architecture

You can extend DSF for:

- Multi-step pipeline: extract → transform → enrich → publish
- Lakehouse combines Glue Catalog + Iceberg/Hudi
- Real-time ingestion with Kinesis/Managed Kafka
- Combined with Lake Formation data governance

DSF creates a unified platform to scale according to business needs.

---

## Conclusion

**Data Solutions Framework on AWS** helps standardize the entire Spark application development lifecycle, from local development to production deployment.
In an environment where data workloads are increasingly complex, DSF helps data engineering teams:

- Reduce development costs
- Avoid errors due to lack of standardization
- Increase productivity and deployment speed
- Ensure consistency across Spark pipelines
- Easily integrate with EMR, Step Functions, MWAA, and CI/CD

DSF is not simply a tool, but a **best-practice framework** that helps businesses build a powerful, flexible, and scalable data processing platform.

---