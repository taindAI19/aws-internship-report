---
title: "Week 12 Worklog"
weight: 2
chapter: false
pre: " <b> 1.12 </b> "
---

### Objectives for the week

**Part 1 – Introducing Amazon Bedrock & Foundation Models**

* Understand how Amazon Bedrock is designed and the main operating components.
* Learn how to access and use foundation models through Bedrock.
* Survey popular models such as Claude, Llama, Mistral, Amazon Titan…
* Understand the difference between text generation models, embedding models, and multimodal models.

**Part 2 – Building AI Agents with Bedrock Agent**

* Understand the concept of AI Agents and how they work.
* Understand the components:

* Action groups
* Knowledge bases
* Orchestration
* Integrate Lambda functions

* Set up an AI Agent that can call and use tools through Lambda.

**Part 3 – Using Knowledge Base for Enterprise Search**

* Create a Knowledge Base using vector embeddings.
* Link Bedrock KB to data stored in S3.

* Test semantic search capabilities and RAG (Retrieval Augmented Generation) mechanism.

* Complete KB integration into Bedrock Agent.

**Part 4 – Integrate Front-end with Bedrock Agent**

* Build a chat interface to interact directly with the Agent.

* Implement streaming data to display real-time responses.

* Describe the processing flow: User input → Agent → (KB, Lambda) → Returned results.

* Bring the front-end to the Amplify Hosting environment.

---

### Deployment tasks of the week

### Deployment Tasks of the Week

| Day | Task Details | Start Date | Completion Date | Resources |
| --- | ------------------- | ------------ | ---------------- | --------------- |
| 2 | **Understanding the Bedrock Platform**<br>• Explore the model list.<br>• Try Claude / Llama 3 in Playground.<br>• Compare costs and performance.<br>• Understand the basic Bedrock API. | 2025-11-24 | 2025-11-24 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | **Develop a simple Text Generation application**<br>• Write a Lambda that calls the InvokeModel API.<br>• Test temperature and max tokens.<br>• Create a small CLI using the SDK. | 2025-11-25 | 2025-11-25 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | **Set up Bedrock Agent**<br>• Configure agent.<br>• Create instructions and guardrails.<br>• Create Action Group using Lambda.<br>• Connect agent to sample DynamoDB. | 2025-11-26 | 2025-11-26 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | **Build Knowledge Base (RAG) system**<br>• Create S3 bucket to store documents.<br>• Set up embeddings (Titan Embeddings G1).<br>• Test Q&A with PDF/CSV.<br>• Integrate KB into Agent. | 2025-11-27 | 2025-11-27 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | **Test the entire Agent**<br>• Test the chain of operations: Agent → KB → Lambda.<br>• Fix IAM, KMS errors.<br>• Test multiple conversations.<br>• Add error handling and fallback. | 2025-11-28 | 2025-11-28 | <https://cloudjourney.awsstudygroup.com/> |
| 7 | **Develop Chat interface using Amplify**<br>• Create React Chat UI.<br>• Connect to Agent via API Gateway.<br>• Test streaming output.<br>• Deploy using Amplify Hosting. | 2025-11-29 | 2025-11-29 | <https://cloudjourney.awsstudygroup.com/> |
---

### Results achieved in week 12

**1. Knowledge of Amazon Bedrock & Foundation Models**

* Know how to call models via Bedrock SDK.
* Practice with different model groups.

* Understand application scenarios: text generation, summarization, code generation, embeddings.

---

**2. Complete a real-world AI Agent**

* Agent recognizes user intent.

* Use Action Groups to trigger Lambda.
* Support multi-step inference.
* Query DynamoDB via Lambda.

---

**3. Build a Knowledge Base for RAG**

* Create a vector repository from data in S3.
* Perform semantic search successfully.
* Agent improves response quality when integrating KB.

---

**4. Create a chat interface that works with Bedrock**

* Build a chat UI using React.
* Connect via API Gateway for security.
* Work well with streaming responses.
* Full flow: UI → Agent → KB/Lambda → Response.

---

### Summary of knowledge learned

**Amazon Bedrock**

* Provides access to many powerful models.
* Fully managed and enterprise-grade security system.
* Supports document generation, embeddings, and multi-modal models.

**Bedrock Agents**

* Capable of maintaining conversations, processing logic, and calling tools.
* Action Groups enable real-world backend connections.
* Guardrails help secure content control.

**Knowledge Bases**

* Embeddings enhance semantic search capabilities.
* Combine KB and Agent to form a complete RAG system.
* Supports automatic document updates from S3.

**Integration & Deployment**

* Lambda executes backend logic.
* API Gateway ensures secure connections for the front-end.

* Amplify supports rapid interface deployment.

---