---
title: "Week 4 Worklog"
date: "2025-10-05"
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Week 4 Objectives:

- Master foundational + advanced Networking knowledge on AWS
- Practice deploying Compute & Container services
- Improve skills in building Serverless applications

### Tasks to be carried out this week:

| Day | Tasks                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | Start Date | Completion Date | Reference Material                  |
| --- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------- | ----------------------------------- |
| 2   | - **Deploy Lightsail Database:** <br> &emsp; + Deploy Wordpress Instance <br> &emsp; + Create and configure instances <br> &emsp; + Deploy three open-source applications on Lightsail: WordPress, PrestaShop, Akaunting <br> &emsp; + Configure networking: assign static IP for VM <br> &emsp; + Configure application security <br> &emsp; + Create snapshot/backup for database and instance <br>&emsp; + Scale to larger instance: manually create snapshot of current instance <br>&emsp; + Create system monitoring alerts                                                                                           | 29/09/2025 | 29/09/2025      | <https://000045.awsstudygroup.com/> |
| 3   | - **Deploy AWS Lightsail Container Service** <br>&emsp; + Create a Lightsail Container Service on AWS <br>&emsp; + Upload container image to Lightsail <br>&emsp; + Create Lightsail instance <br>&emsp; + Install Docker on Lightsail instance <br>&emsp; + Build and push container image to Lightsail store <br>&emsp; + Deploy container                                                                                                                                                                                                                                                                                | 30/09/2025 | 30/09/2025      | <https://000046.awsstudygroup.com/> |
| 4   | - **Practice DynamoDB on AWS Management Console** <br>&emsp; + Create table, write data, read data, update, query <br>&emsp; + Create Global Secondary Index <br>&emsp; + Use AWS CloudShell <br>&emsp; + Create table, write/read/update/query data <br>&emsp; + Create Global Secondary Index <br>&emsp; + Use AWS SDK (CRUD) <br>&emsp; + Configure AWS CLI                                                                                                                                                                                                                                                              | 01/10/2025 | 01/10/2025      | <https://000060.awsstudygroup.com/> |
| 5   | - **Practice Amazon ElastiCache:** <br>&emsp; + Create VPC, subnet group, and security group for ElastiCache <br>&emsp; + Create ElastiCache Cluster (Redis or Memcached) <br>&emsp; + Configure node type, number of nodes, parameter settings <br>&emsp; + Connect EC2 → ElastiCache via private endpoint <br> - Write code/CLI: Set key/value, Get key/value, Delete key <br>&emsp; + Create replication group, test failover (for Redis) <br>&emsp; + Test performance difference with/without caching                                                                                                                  | 02/10/2025 | 02/10/2025      | <https://000061.awsstudygroup.com/> |
| 6   | - **Practice Networking services on AWS:** <br>&emsp; + Create VPC, route table, subnet, Internet Gateway <br>&emsp; + Create Security Group & Network ACL <br>&emsp; + Launch EC2 in public/private subnet, connect via SSH <br>&emsp; + Configure Application Load Balancer: Target group, Listener, Health check <br>&emsp; + Deploy Auto Scaling Group attached to ALB <br>&emsp; + Configure scaling policies <br>&emsp; + Create CloudFront Distribution <br>&emsp; + Configure Behavior rules, Cache TTL <br>&emsp; + Test CDN access via CloudFront domain <br>&emsp; + Test access acceleration through CloudFront | 03/10/2025 | 03/10/2025      | <https://000092.awsstudygroup.com/> |

### Week 4 Achievements:

- Able to deploy database + VM + complete applications on Lightsail, from backend to frontend, sufficient to run websites, e-commerce, and enterprise applications.
- Understood NoSQL data model of DynamoDB: concepts of table, item, attribute; understanding Primary Key, Secondary Index, supported data types (scalar, document, set)
- ElastiCache works as an in-memory cache to accelerate applications, able to deploy Redis/Memcached inside VPC
- Mastered AWS Networking architecture: VPC, route, IGW, NAT, security layers
