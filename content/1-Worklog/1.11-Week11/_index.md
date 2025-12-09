---
title: "Worklog Week 11"
date: "2025-11-23"
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Week 11 Objectives:

- Fully deploy all services defined in the project

### Tasks to be carried out this week:

| Day | Tasks                                 | Start Date | Completion Date | Reference Material |
| --- | ------------------------------------- | ---------- | --------------- | ------------------ |
| 2   | - Work on the project and test errors | 17/11/2025 | 17/11/2025      |                    |
| 3   | - Work on the project and test errors | 18/11/2025 | 18/11/2025      |                    |
| 4   | - Work on the project and test errors | 19/11/2025 | 19/11/2025      |                    |
| 5   | - Work on the project and test errors | 20/11/2025 | 20/11/2025      |                    |
| 6   | - Work on the project and test errors | 21/11/2025 | 21/11/2025      |                    |

### Week 11 Achievements:

- Wrote project code and tested errors
- Built, deployed, and managed a Serverless application using IaC templates with AWS SAM/CloudFormation, API Gateway, DynamoDB, Cognito, invite/redeem, and Google SSO
- Set up comprehensive monitoring and alerting with CloudWatch:
  - Created `monitoring-alarms.yaml` for both Identity and Academic services
  - Lambda alarms: Error rate > 5%, Execution time > p99, Throttles, Concurrent executions
  - API Gateway alarms: 4XX client errors, 5XX server errors, Latency
  - DynamoDB alarms: Read/write throttles, Consumed capacity
  - SNS topic: `tcm-pipeline-notifications` for sending alerts
  - Subscribed email to receive real-time notifications
  - CloudWatch dashboard for visualizing metrics (can be added later)
  - 30-day retention policy to optimize cost
