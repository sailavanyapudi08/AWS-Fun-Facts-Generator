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

# Hardcoded logic --> Database-backed flexibility
- create a lambda function with facts hardcoded
- create HTTP API gateway to access the lambda backend service through URL by connecting the lambda with API Gateway
- Create a DynamoDB and populate the database with facts.
- Later, instead of editing Lambda code, we can just add more rows here.
- By default, our Lambda cannot talk to DynamoDB. We must grant it permission: "that is because AWS follows least privilege principle."
- Attach an IAM role: AmazonDynamoDBReadOnlyAccess to the role we created for Lambda function. So that  we’re allowing Lambda to read items but not modify/delete them (safer).
- Update Lambda code so that it reads the dynamo table that we created earlier.
