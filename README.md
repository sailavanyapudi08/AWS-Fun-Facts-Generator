# AWS-Fun-Facts-Generator
The aws fun facts generator is an app which generates random cloud facts. we will connect multiple AWS services to make it dynamic, scalable and interactive.

## Steps to Build and Deploy

This project is developed in four main stages:

1. Backend Deployment – Build and deploy the backend using **AWS Lambda** and **API Gateway**.  
2. Database Integration – Add **Amazon DynamoDB** to store and manage fun facts efficiently.  
3. GenAI Enhancement – Integrate **Amazon Bedrock (Generative AI)** to make facts more engaging and witty.  
4. Frontend Deployment – Use **AWS Amplify** to host and display the enhanced facts on a responsive web interface.

## Services Used
- AWS Lambda  
- Amazon API Gateway  
- Amazon DynamoDB  
- Amazon Bedrock  
- AWS Amplify  
- AWS IAM

Question: Why cant we use a load balancer before lambda?
Ans: Use API Gateway when you’re building a serverless API. Use ALB when you’re mixing Lambda with traditional compute (EC2/ECS) or need load balancing, not API management.
