---
title : "Introduction"
date :  "2025-09-15" 
weight : 1 
chapter : false
pre : " <b> 5.1. </b> "
---

#### Workshop Introduction

This workshop guides you through building a **serverless Excel Import** system on AWS with authentication and data processing features.

#### Objectives

By the end of this workshop, we will:

- **Get familiar with serverless architecture:** How to design applications with Lambda, API Gateway, S3, and DynamoDB
- **Get familiar with event-driven architecture:** Use S3 Event Notifications to trigger automatic processing
- **Implement authentication:** Integrate Amazon Cognito for authentication and API security
- **Parse Excel in Lambda:** Use the Apache POI library to read and process .xlsx/.xls files
- **Deploy with AWS SAM:** Get familiar with the SAM CLI to build and deploy, and apply IaC for the entire infrastructure. 

#### Key Components

- **8 Lambda Functions:** Register, Confirm, Login, Logout, GenerateUploadUrl, ListImportJobs, GetJobStatus, ImportS3Trigger
- **3 DynamoDB Tables:** Students, Courses, ImportJobs
- **1 S3 Bucket:** Store Excel files with a lifecycle policy (auto-delete after 7 days)
- **1 Cognito User Pool:** Manage users and authentication
- **1 API Gateway:** REST API with a Cognito authorizer

#### Time & Cost

**Estimated completion time:** ~30 minutes

**Cost:** Free (All within the Free Tier)

> To avoid unexpected charges, perform cleanup immediately after finishing the workshop.

#### Requirements

- Basic understanding of AWS (console, regions, basic services)
- Ability to use the terminal/command line
- Ability to read Java

```