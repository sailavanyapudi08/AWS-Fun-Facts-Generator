# AWS-Fun-Facts-Generator
The aws fun facts generator is an app which generates random cloud facts. we will connect multiple AWS services to make it dynamic, scalable and interactive.

## Steps to Build and Deploy

This project is developed in four main stages:

1. Backend Deployment – Build and deploy the backend using **AWS Lambda** and **API Gateway**.  
2. Database Integration – Add **Amazon DynamoDB** to store and manage fun facts efficiently.  
3. GenAI Enhancement – Integrate **Amazon Bedrock (Generative AI)** to make facts more engaging and witty.  
4. Frontend Deployment – Use **AWS Amplify** to host and display the enhanced facts on a responsive web interface.

## Services Used
- AWS Lambda - Serverless Backend
- Amazon API Gateway - exposes lambda as a rest API end point
- Amazon DynamoDB - Database
- Amazon Bedrock - Gen AI to generate facts
- AWS Amplify - Frontend hosting service
- AWS IAM - for secure permissions

Question: Why cant we use a load balancer before lambda?

Ans: Use API Gateway when you’re building a serverless API. Use ALB when you’re mixing Lambda with traditional compute (EC2/ECS) or need load balancing, not API management.

# Architecture:

<img width="429" height="300" alt="Screenshot 2025-10-22 at 5 28 46 PM" src="https://github.com/user-attachments/assets/ade81a2a-6318-4d42-b30c-0b92fa8ff8a9" />

## Steps to Build

### Stage 1: Hardcoded Lambda
- Create a Lambda function that returns a hardcoded fact.

### Stage 2: API Gateway
- Create an HTTP API and connect it to Lambda.  
- Deploy and get your public API endpoint.

### Stage 3: DynamoDB
- Create a table (e.g., `CloudFacts`) and add facts.  
- Attach `AmazonDynamoDBReadOnlyAccess` to Lambda role.  
- Update Lambda to read facts from DynamoDB.

### Stage 4: AI Enhancement
- Attach `AmazonBedrockFullAccess` to Lambda role.  
- Update Lambda code to send facts to Bedrock models for funny or engaging output.  

### Stage 5: Frontend with Amplify
- Create `index.html` to call your API and show facts.  
- Enable CORS on API Gateway:  
  - Allowed origins: your Amplify domain (or `*` for testing)  
  - Allowed methods: GET, OPTIONS  
  - Allowed headers: Content-Type, Authorization, X-Amz-Date, X-Api-Key, X-Amz-Security-Token  
- Deploy the frontend to Amplify by uploading a ZIP with `index.html`.  
- Open the Amplify URL and test your app.

---

## IAM Permissions

| Service | Policy |
|---------|--------|
| DynamoDB | AmazonDynamoDBReadOnlyAccess |
| Bedrock | AmazonBedrockFullAccess |
| CloudWatch Logs | Default for Lambda |

---

## Requirements

- AWS Account with Lambda, API Gateway, DynamoDB, and Bedrock access  
- AWS Amplify for hosting  

---

## Future Improvements

- Add user-submitted facts with POST requests  
- Add authentication with Cognito  
- Convert frontend to React + Amplify CI/CD  
- Deploy backend using AWS SAM or CDK  


