---
title: "Week 11 Worklog"
weight: 2
chapter: false
pre: " <b> 1.11. </b> "
---

---

### Week 11 Objectives:

#### Part 1 – Serverless with Amplify Authentication and Storage

- Learn how Amplify Libraries work, especially Amplify Auth and Storage.
- Connect a web application to Cognito to manage users.
- Build a frontend upload function and save files directly to S3 via Amplify Storage.
- Understand the three file access modes: public, protected, and private.
- Understand the communication mechanism between Cognito – S3 – Amplify in a serverless application.

#### Part 2 – Serverless: Build a Frontend that communicates with an API Gateway

- Understand how to create an API Gateway and map requests to Lambda.
- Write frontend (JavaScript/React) to call API Gateway → Lambda → DynamoDB.

- Test API using Postman and from frontend itself.

- Understand the entire data path process:
**Frontend → API Gateway → Lambda → DynamoDB**.

---

### Work done this week

| Day | Contents | Start | Finish | Source |
| --- | -------- | ------- | ---------- | ------ |
| 2 | **Starting Amplify and Preparing the Environment**<br>• Learn about Amplify Libraries, CLI, and UI Components.<br>• Initialize an Amplify integration project.<br>• Install `aws-amplify` and `@aws-amplify/ui`.<br>• Configure AWS locally. | 11/17/2025 | 11/17/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | **Authenticate users with Amplify Auth**<br>• Create a User Pool and Identity Pool.<br>• Configure Amplify Auth in the frontend.<br>• Use Amplify UI Components to create a login interface.<br>• Test the flow of creating an account, logging in, confirming the code, and changing the password. | 11/18/2025 | 11/18/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | **Store files via Amplify Storage**<br>• Create an S3 bucket using Amplify.<br>• Set up public/protected/private access rights.<br>• Write an upload function from the frontend to S3.<br>• Test again on the S3 console.<br>• Write logic to list files and get the URL. | 11/19/2025 | 11/19/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | **Create an API Gateway to connect Lambda**<br>• Build a REST API.<br>• Attach CRUD routes to Lambda.<br>• Enable CORS for the frontend.<br>• Update new ARNs for Lambda functions. | 20/11/2025 | 20/11/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | **Test API with Postman**<br>• Send requests with GET/POST/DELETE methods.<br>• Attach Cognito token in header.<br>• Monitor logs with CloudWatch.<br>• Fix CORS errors and IAM permissions. | 21/11/2025 | 21/11/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 7 | **Integrate frontend with API Gateway**<br>• Write JS service to call API Gateway.<br>• Automatically attach Cognito token.<br>• Display data returned from Lambda/DynamoDB.<br>• Complete end-to-end process: Frontend → API → Lambda → DynamoDB.<br>• Clean up test data. | 11/22/2025 | 11/22/2025 | <https://cloudjourney.awsstudygroup.com/> |

---

### Results achieved in week 11

#### 1. Successfully set up Authentication using Amplify + Cognito

- Complete all flows: login, registration, code authentication and password reset.

- Frontend gets JWT token to use when calling API Gateway.

- Understand how Cognito manages identity through User Pool and Identity Pool.

---

#### 2. Store and manage files using Amplify Storage + S3

- Upload files directly from frontend to S3 successfully.

- S3 bucket is automatically created by Amplify.

- Fully test 3 types of access rights.

- Complete file processing functions: upload, list, get URL, and delete option.

---

#### 3. Build API Gateway to serve DMS system

- Create complete REST API with CRUD routes.

- Connect directly to Lambda from last week.
- Configure standard CORS for frontend.

- Send request with JWT token and test everything with Postman.

---

#### 4. Integrate frontend with API Gateway

- Write frontend logic to send request with Cognito token.

- Display metadata list from DynamoDB.
- Complete the overall flow:

---

### Summary of the week

#### Amplify
- Amplify Auth uses Cognito as the authentication system.

- Amplify Storage supports simple S3 operations from the frontend.

- UI component set helps create a quick login page.

#### Cognito (Authentication)
- User Pool: account management.
- Identity Pool: grants access to AWS resources.
- JWT token used when sending requests to API Gateway.

#### S3 (Storage)
- Support file permissions according to public / protected / private.
- Upload directly from the client via Amplify.

#### API Gateway
- Coordinate requests to Lambda.
- CORS is important for the frontend to work.

- Can require authentication using Cognito tokens.

#### Lambda + DynamoDB
- Lambda executes CRUD functions.
- DynamoDB stores document metadata.
- Frontend only communicates via API Gateway.

---