---
title: "Proposal"
date: 2025-09-30
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# Teaching Center Management System 
## AWS Serverless Solution for Teaching Center Management Project

### 1. Executive Summary
The project focuses on deploying an LMS (Learning Management System) platform serving core training operations, equivalent in scope to systems like lms-hcmuni.fpt.edu.vn. Specifically, the scope includes 2 main parts: academic management and authentication/identification and authorization.

The goal is to provide essential LMS capabilities: managing courses and classes; class schedules; searching and enrollment using enrollKey; role-based dashboards (Admin, Teacher, Student); managing instructor/student profiles; managing course documents on S3 (creating folders, uploading, downloading with enrollment verification); and batch data import from Excel to quickly initialize academic data. The authentication/identification and authorization part ensures login/authentication with Amazon Cognito (supporting OAuth/Google), invitation/redemption of invitations, password reset/change, token refresh, user profiles, and role-based authorization mechanisms to protect academic resources.

<!-- Suggestion (not displayed in main version): Can add LMS features such as attendance, assignments, grading, announcements, quizzes/exams, class schedule export, etc. if needed for future expansion. -->

In the future, the system can gradually expand to other modules (CRM, payments, HRM, etc.) and consider integrating AI/IoT when needed, but these are not within the scope of the current deployment.

### 2. Problem Statement
**Current Issues**

In the LMS context, many training units operate in silos with discrete steps: creating courses/classes, publishing schedules, enrolling students, managing documents, and accessing profiles — typically across multiple different tools. This leads to fragmented data, difficult access control, manual enrollment processes (prone to errors), and inconsistent user experience between instructors and students.

As the number of courses/classes increases, there's a lack of unified role-based authorization mechanisms, reliable authentication (SSO/OAuth), and clear academic APIs to support role-based dashboards. The absence of batch data import channels also causes delays when initializing new semesters.

**Solution**

The platform is deployed on AWS Serverless architecture, focusing on addressing two main pillars:
- Authentication/Identification and Authorization: Amazon Cognito for authentication (email/password, Google OAuth), invitations (invite/redeem), password reset/change, token refresh, user profiles; role-based authorization (ADMIN/TEACHER/STUDENT) to protect APIs and academic resources.
- Academic Management: APIs for managing courses/classes, unified search, enrollment using enrollKey (activating PRE_ENROLLED → ACTIVE), role-based dashboards, instructor/student profiles, and course document management on S3 (creating folders, presigned upload/download with enrollment verification). Supports Excel import for quick data initialization and full rollback on errors.

<!-- Suggestion (not displayed in main version): Can add descriptions for attendance, assignments, grading, announcements, quizzes to facilitate easy expansion into a full LMS in the next phase. -->

The access flow: CloudFront → S3 (static content) and API Gateway → Lambda → DynamoDB (academic/identity data) with CloudWatch/SNS/Secrets Manager for monitoring and security. CI/CD is implemented through GitLab Runner combined with AWS SAM CLI.

**Benefits and Return on Investment (ROI)**

- *Accelerated development and deployment*: Automated CI/CD with GitLab Runner and CloudFormation reduces feature release time from days to hours.
- *Optimized operational costs*: Serverless architecture (Lambda, DynamoDB, API Gateway) charges only per request, saving 40–60% of costs compared to traditional EC2.
- *Comprehensive security*: Secrets Manager and Cognito combined with IAM provide robust protection for sensitive data and strict access control.
- *High access performance*: CloudFront CDN accelerates access and reduces latency by 50–70%.
- *Flexible scalability*: The system automatically scales according to traffic without manual intervention.
- *Proactive monitoring*: CloudWatch + SNS provides real-time alerts, helping the technical team respond promptly to incidents.

### 3. Solution Architecture

![Teaching center management](/images/2-Proposal/project1_architecture_diagram.jpg)

#### Detailed Description

1.  **User Request Flow**
    -   Users open a browser and access the application through a domain.
    -   **Amazon CloudFront** receives the request:
        +   Checks the cache to return static content (HTML/CSS/JS) from **S3** if available.
        +   If content is not in cache, CloudFront fetches from S3 and returns it to the user with low latency.
    -   Users receive the frontend and interact with the UI, generating API requests.

2.  **Authentication & API Handling**
    -   When users log in:
        +   **Amazon Cognito** authenticates login information (username/password or OAuth).
        +   Cognito generates a JWT token and returns it to the client.
    -   The frontend sends API requests with the JWT token to **API Gateway**.
    -   API Gateway performs:
        +   Verifies the JWT token with Cognito.
        +   If the token is valid, the request is forwarded to the corresponding Lambda function.
        +   If the token is invalid, API Gateway returns a 401 Unauthorized error.

3.  **Lambda Processing & Data Access**
    -   **AWS Lambda** executes business logic:
        +   Manages students, attendance, course registration, updates results, schedules…
        +   When accessing sensitive information (API keys, DB passwords), Lambda calls **AWS Secrets Manager**.
    -   Lambda reads/writes data to **Amazon DynamoDB**:
        +   DynamoDB stores data in a NoSQL model, optimized for read/write, automatically scaling when traffic increases.
        +   Supports queries using primary key (PK) or secondary index (GSI).
    -   Lambda logs to **CloudWatch Logs**, including requests, errors, and execution metrics.

4.  **Security & Access Control**
    -   **Amazon Cognito**: authenticates users and manages sessions, supporting OAuth/Google Sign-In.
    -   **IAM Roles & Policies**: control access permissions between AWS services (Lambda, DynamoDB, S3).
    -   **API Gateway Authorization**: validates JWT tokens from Cognito before allowing Lambda access.
    -   **Secrets Manager**: protects sensitive information (API keys, database credentials), enabling secure Lambda access.

5.  **Monitoring & Alerts**
    -   **CloudWatch Logs** collects logs from Lambda and API Gateway.
    -   **Metrics & Alarms**:
        +   Creates metrics from logs (CPU, error rate, latency, request count).
        +   Configures CloudWatch Alarms to trigger alerts when thresholds are exceeded.
    -   **Amazon SNS** sends real-time alerts to the operations team via email or HTTP/SMS endpoints.
    -   Combines CloudTrail + CloudWatch for auditing API actions and overall security.

6.  **CI/CD & Deployment**
    -   **GitLab**: stores source code and manages version control.
    -   **GitLab Runner**:
        +   Automatically triggers on code push or merge request.
        +   Runs CI/CD pipeline with stages: test, build, deploy.
        +   Installs dependencies and runs unit tests.
        +   Builds artifacts (ZIP package for Lambda).
    -   **AWS SAM CLI / CloudFormation**:
        +   GitLab Runner uses AWS SAM CLI for deployment.
        +   Deploys or updates the entire AWS infrastructure (API Gateway, Lambda, DynamoDB, S3, IAM Role).
        +   Ensures infrastructure follows IaC model, consistent across Dev/Prod environments.
    -   Automated CI/CD reduces errors and shortens deployment time.

7.  **Summary**
    -   **Request Path**: User → CloudFront → API Gateway → Lambda (via Cognito Auth) → DynamoDB → Lambda → API Gateway → CloudFront → User.
    -   **Security Path**: Cognito Authentication → API Gateway Authorization → IAM Policies → Secrets Manager.
    -   **Monitoring**: CloudWatch Logs & Metrics → Alarms → SNS.
    -   **CI/CD Path**: GitLab → GitLab Runner → AWS SAM CLI → CloudFormation → AWS Resources.

#### AWS Services Used
|                   | Services                                                                           | Description                                        |
| ------------------------- | ---------------------------------------------------------------------------------- | -------------------------------------------------- |
| **Frontend & CDN**    | CloudFront, S3                                                           | Content distribution, static storage    |
| **Backend & Logic**       | API Gateway, Lambda, DynamoDB, Secrets Manager, Cognito                            | Serverless logic, data, authentication        |
| **Monitoring** | CloudWatch Logs, CloudWatch Alarms, CloudWatch Metrics, SNS | Monitoring, alerts, metrics collection                   |
| **CI/CD & IaC**           | CloudFormation, SAM                                       | Automated deployment and infrastructure management (with GitLab Runner)  |
    
### 4. Technical Implementation
*Deployment Stages*  
- Development Stage
    + Complete business logic and main flow for Lambda functions.
    + Write `template.yaml` file describing resources: API Gateway, Lambda Functions, DynamoDB, Cognito.
    + Use AWS SAM CLI to deploy code and `template.yaml` to LocalStack for local testing.
- Deployment Stage:
    + Use AWS SAM CLI to deploy code and `template.yaml` to the real AWS environment.
    + Configure GitLab CI/CD with GitLab Runner to automate the build and deployment process.

*Technical Requirements*  
- Have an AWS account using Free Tier to deploy and use resources normally.
- The `template.yaml` file must be correctly configured to fully describe all services.
- The system must have an automatic rollback mechanism in case of deployment failure.

### 5. Roadmap & Deployment Milestones
- *Pre-Internship (Week 0)*: Learn AWS services to prepare for the project. Survey, analyze requirements and related departments of real centers (HR, Training, Admissions).
- *Internship (Week 1-12):*
    + Week 1–3: System design, UI design, overall architecture, and prepare documentation (proposal, diagrams, SAM template).
    + Week 4–8: Develop core modules (student management, instructor management, class management, user authentication). Local testing using LocalStack.
    + Week 9–11: Integrate modules, finalize CI/CD pipeline, deploy the system to the real AWS environment.
    + Week 12: End-to-end testing, evaluate results, complete report, and propose future development directions.
- *Post-Internship (Expansion Phase – Week 12 onwards): Upgrade the system, optimize performance, and integrate AI (personalized learning analytics) and IoT (smart classroom management).*

### 6. Budget Estimation
You can view costs on [AWS Pricing Calculator](https://calculator.aws/#/estimate?id=124ba62af284b2bb59152497a349995d8342c2a5)  
Or download the budget estimate files [pdf](/files/project_1_estimate.pdf) | [csv](/files/project_1_estimate.csv) | [json](/files/project_1_estimate.json)  

*Infrastructure Costs*

- S3 Standard: 0.32 USD/month (10 GB, 5,000 PUT requests, 100,000 GET requests).
- CloudFront: 1.33 USD/month (10 GB, Data transfer out to origin 0.1 GB, Number of HTTPS requests 100,000).
- Amazon API Gateway: 0.38 USD/month (300,000 requests).
- AWS Lambda Function - Include Free Tier: 0.00 USD/month (400,000 requests, 512 MB storage).
- Amazon DynamoDB: 0.62 USD/month (Data storage 2 GB, 50,000 Writes, 200,000 Reads)
- Amazon Cognito Lite Tier: 0.00 USD/month (500 MAUs)
- Amazon CloudWatch: 2.10 USD/month (3 custom metrics, 1 GB logs, 1 dashboard, 2 alarms)
- AWS Secrets Manager: 0.40 USD/month (1 secret)
- Amazon SNS: 0.00 USD/month (1M requests, 1M Lambda deliveries)
- AWS CloudFormation: 0.00 USD/month
- GitLab Runner: 0.00 USD/month (self-hosted or GitLab Free Tier)

 *Total*: 5.15 USD/month, 61.80 USD/12 months

### 7. Risk Assessment
*Risk Matrix*
- AWS configuration errors (IAM, Lambda, API Gateway, Cognito): High impact, medium probability
- Exceeding AWS Free Tier limits: Medium impact, low probability.
- Data loss on S3/DynamoDB: High impact, low probability.
- Integration errors between AWS services: Medium impact, low probability.
- External attacks (SQL injection, XSS, unauthorized access): High impact, low to medium probability

*Mitigation Strategies*
- AWS Configuration: Carefully check `template.yaml`, deploy on LocalStack before production deployment.
- Free Tier Exceeding: Monitor costs regularly, set up Billing Alerts, optimize resources.
- Data Loss: Enable S3 Versioning, periodically backup DynamoDB data.
- Service Integration Errors: Ensure services operate in the same Region, verify IAM Roles and cross-service access permissions.
- Application Security: Validate input at Lambda layer, use Cognito for strict authentication, configure CORS properly on API Gateway, apply principle of least privilege for IAM roles, enable CloudWatch and API Gateway logging for auditing.

*Contingency Plan*
- Deployment failures: Rollback using AWS SAM CLI or restore previous Lambda version through CloudFormation stack.
- Budget overrun: Pause non-essential services, optimize architecture and resource usage.
- Security incidents: Review CloudWatch logs, disable compromised users/tokens via Cognito, review IAM permissions, isolate affected Lambda functions.

### 8. Expected Outcomes
- The teaching center management system is successfully deployed on AWS Serverless, ensuring stable, secure, and scalable operations.
- Optimize operational costs by leveraging AWS Free Tier and serverless architecture, reducing initial infrastructure investment.
- Ensure high access performance, fast response time, and flexible scalability.
- Guarantee data safety with backup, versioning, and strict access control mechanisms.
- CI/CD integration automates deployment, testing, and rollback, ensuring efficient and reliable development processes.
