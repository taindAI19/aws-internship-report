---
title: "Week 10 Worklog"
weight: 2
chapter: false
pre: " <b> 1.10. </b> "
---

---

### Week 10 Objectives:

#### Part 1 – Building a backend Document Management System (DMS) with Lambda and DynamoDB

- Understand the operational architecture of a document management system.
- Design DynamoDB tables based on the actual access needs of the application.
- Write Lambda Functions to create new, get lists, query details and delete documents.
- Configure IAM Role for Lambda according to the principle of minimal rights.
- Conduct testing through test events and monitor with CloudWatch Logs.
- Prepare the backend to integrate API Gateway and Amplify next week.

#### Part 2 – Understand how DMS will be extended in the coming weeks

- Understand the role of Cognito, Amplify Storage in the system.
- Know how DynamoDB Streams are used to synchronize data to OpenSearch for search.
- Visualize how the entire backend will be deployed using AWS SAM.
- Understand the expected CI/CD flow running on AWS CodePipeline.

---

### Work done this week

| Day | Implementation content | Start | Complete | Source |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------- | ---------- | ------ |
| 2 | **Analyze the entire DMS architecture**<br>• Clarify the goals: upload, view, download, delete and search documents.<br>• Identify the main services: Lambda, DynamoDB, S3, Cognito, API Gateway.<br>• Analyze the processing flow from uploading to saving metadata and serving search.<br>• Build a list of APIs needed for the backend. | 10/11/2025 | 10/11/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | **Designing a DynamoDB table for document metadata**<br>• Create a `Documents` table (PK: `userId`, SK: `documentId`).<br>• Define attributes such as filename, fileType, size, tags, createdAt, updatedAt.<br>• Analyze access patterns: query by user, get details by documentId, filter by tag.<br>• Prepare sample data and test using Console/CLI. | 11/11/2025 | 11/11/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | **Create IAM Role for Lambda**<br>• Initialize the role `DMSLambdaRole`.<br>• Grant DynamoDB CRUD permissions (GetItem, Query, PutItem, DeleteItem).<br>• Enable logging to CloudWatch Logs.<br>• Review the trust policy for Lambda.<br>• Confirm the role works correctly by testing directly in Lambda. | 11/12/2025 | 11/12/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | **Write Lambda CreateDocument**<br>• Check user input.<br>• Generate `documentId` as UUID.<br>• Save metadata to table via `put_item`.<br>• Log for monitoring.<br>• Test via test event and CloudWatch Logs.<br>• Handle missing input, DynamoDB errors or unusual errors. | 11/13/2025 | 11/13/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | **Write Lambda GetDocuments and GetDocumentById**<br>• Write logic to query all documents by userId.<br>• Add pagination capability using LastEvaluatedKey.<br>• Write function to get details of a document by documentId.<br>• Normalize the returned JSON to match the front-end.<br>• Test with real data in DynamoDB. | 11/14/2025 | 11/14/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 7 | **Write Lambda DeleteDocument and cleanup data**<br>• Check the existence of the document before deleting.<br>• Delete metadata using `delete_item`.<br>• Prepare logic to delete S3 file (will do next week).<br>• Log details of the deletion process.<br>• Clean up unused test records. | 11/15/2025 | 11/15/2025 | <https://cloudjourney.awsstudygroup.com/> |
---

### Results achieved in week 10

#### 1. Complete the DynamoDB table with the optimal model

- Build the `Documents` table to fully meet the metadata storage needs of DMS.
- Design a partition/sort key suitable for querying by user and getting document details.
- Data structure is easy to extend to DynamoDB Streams or integrate OpenSearch.

---

#### 2. Complete the Lambda CRUD set for the system

- Create new documents using CreateDocument.
- Get list of documents by userId using GetDocuments.
- Query details using GetDocumentById.
- Delete documents using DeleteDocument.
- All logic is serverless, logs are clear and reprocesses when errors occur.

---

#### 3. Implement best practices for security and monitoring

-IAM Role is configured according to the principle of “least privilege”.

- CloudWatch Logs serve to monitor the entire processing process.

- Error handler is clear enough: input error, DynamoDB error or non-existent record.

---

#### 4. Fully understand the overall architecture of the DMS system

- Understand the connection between Authentication – API – Storage – Metadata.

- Know how Lambda will be integrated into API Gateway next week.

- Have a technical foundation to continue with Amplify Authentication and Storage next week.

---

### Summary of knowledge in the week

#### AWS DynamoDB
- Design tables according to access patterns.

- Use Partition/Sort Key correctly.

- Master PutItem, GetItem, Query, DeleteItem (Boto3) operations.

#### AWS Lambda
- Write serverless functions for CRUD.

- Create IAM Roles with appropriate policies.

- Get familiar with logging and monitoring with CloudWatch.
- Handle errors according to production standards.

#### DMS Architecture
- Metadata is in DynamoDB.
- Actual files are stored on S3.
- User authentication with Cognito.
- API routing via API Gateway and Lambda.

---