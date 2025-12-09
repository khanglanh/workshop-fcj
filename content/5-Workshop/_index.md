---
title: "Workshop"
date: "2025-09-15"
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Excel-to-DynamoDB on AWS using S3 Notifications

#### Overview

In this workshop, we will build a complete serverless application to **import data from Excel files to DynamoDB** using AWS services:
- **AWS Lambda** to handle backend logic
- **Amazon S3** to store Excel files
- **S3 Event Notifications** to automatically trigger Lambda when new files arrive
- **Amazon DynamoDB** to store data from excel
- **Amazon Cognito** for user authentication
- **API Gateway** to expose REST APIs

We will perform:
- Deploy serverless application using **AWS SAM**
- Configure S3 Events to trigger Lambda
- Parse Excel files in Lambda and save to DynamoDB
- Integrate Cognito authentication
- Monitor import job progress

#### System Architecture

This workshop implements an event-driven serverless architecture with the following components:

**API Layer:**
- API Gateway with Cognito Authorizer
- REST endpoints for authentication and import operations

**Processing Layer:**
- Lambda functions handling business logic
- S3 Event Notifications trigger processing
- Apache POI library to parse Excel files

**Storage Layer:**
- S3 bucket for file uploads
- DynamoDB tables for data from excel files and import jobs

#### Contents

1. [Workshop Overview](5.1-workshop-overview/)
2. [Environment Setup](5.2-prerequisites/)
3. [System Architecture](5.3-architecture/)
4. [Deploy Backend (AWS SAM)](5.4-deploy-backend/)
5. [Deploy Frontend (React)](5.5-deploy-frontend/)
6. [Test Application](5.6-test-application/)
7. [Cleanup Resources](5.7-cleanup/)
