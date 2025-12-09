---
title: "Week 6 Worklog"
date: "2025-10-19"
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Week 6 Objectives:

- Practice building a Serverless Document Management System (DMS) application
- Improve skills in developing Serverless applications
- Become proficient in hosting web applications

### Tasks to be carried out this week:

| Day | Tasks                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | Start Date | Completion Date | Reference Material                                                                |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------- | --------------------------------------------------------------------------------- |
| 2   | - Build a document management application <br> - Using DMS + Lambda <br>&emsp; + Create table with DynamoDB <br>&emsp; + Create Lambda functions: list, create data, delete data <br>&emsp; + Test the functions                                                                                                                                                                                                                                                                                                          | 13/10/2025 | 13/10/2025      | <https://000133.awsstudygroup.com/>                                               |
| 3   | - Deploy Front-end <br>&emsp; + Set up API Gateway using Lambda function <br>&emsp; + Test API with Postman <br>&emsp; + Test API with Front-end <br><br> - Use Amplify Authentication and Storage <br>&emsp; + Install Amplify CLI <br>&emsp; + Clone sample project from GitHub <br>&emsp; + Initialize Amplify project using `amplify init` <br>&emsp; + Configure Authentication for the application <br>&emsp; + Configure Storage <br>&emsp; + Deploy frontend + backend + test <br>&emsp; + Configure Access Level | 14/10/2025 | 14/10/2025      | <https://000135.awsstudygroup.com/> <br> <br> <https://000134.awsstudygroup.com/> |
| 4   | - **Practice deploying application using SAM:** <br>&emsp; + Install and initialize project using AWS SAM <br>&emsp; + Create User Pool + Identity Pool in Amazon Cognito <br>&emsp; + Create S3 bucket <br>&emsp; + Deploy frontend + backend using SAM & S3 <br>&emsp; + Configure API endpoints + Lambda functions to handle API <br>&emsp; + Test the entire workflow                                                                                                                                                 | 15/10/2025 | 15/10/2025      | <https://000136.awsstudygroup.com/>                                               |
| 5   | - Set up SSL for S3 Static Website <br>&emsp; + Reconfigure the web application using AWS SAM <br>&emsp; + Create Domain and Hosted Zone <br>&emsp; + Prepare source code / project, build & deploy using AWS SAM / AWS CLI <br>&emsp; + Create and configure domain & Hosted Zone with Amazon Route 53 <br>&emsp; + Create SSL certificate with AWS Certificate Manager <br>&emsp; + Create Amazon CloudFront Distribution <br>&emsp; + Deploy static website → test HTTPS + domain + CDN                                | 16/10/2025 | 16/10/2025      | <https://000137.awsstudygroup.com/>                                               |
| 6   | - Practice integrating Amazon OpenSearch with DynamoDB Stream                                                                                                                                                                                                                                                                                                                                                                                                                                                             | 17/10/2025 | 17/10/2025      | <https://000138.awsstudygroup.com/>                                               |

### Week 6 Achievements:

- Understand what AWS is and the basic service groups
- Able to build a full-stack serverless application — front-end hosted on S3, backend using Lambda + API Gateway, data stored in DynamoDB
- Able to use Amplify to build web/mobile serverless applications — without managing servers
- Use CloudWatch to monitor system, collect metrics, logs, create alarms and dashboards for EC2 and applications
- Able to host static websites on S3 + configure SSL/TLS
- Able to set up custom domain + DNS (Route 53) + connect domain with CloudFront & S3 + SSL certificate
- Understand how CDN (CloudFront) integration works
