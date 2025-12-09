---
title: "Week 2 Worklog"
date: "2025-09-21"
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Week 2 Objectives:

- Learn and deploy VPC
- Learn and deploy EC2 Instance inside a VPC
- Configure Hybrid DNS with Route 53 Resolver

### Tasks to be carried out this week:

| Day | Tasks                                                                                                                                                                                                                                                                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                  |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------- | ----------------------------------- |
| 2   | - Deploy VPC and EC2 Instance <br> - **Practice:** <br>&emsp; + Create Subnet, Internet Gateway <br>&emsp; + Create Route Table <br>&emsp; + Create Security Group <br>&emsp; + Enable VPC Flow Logs <br>&emsp; + Launch EC2 Instance <br>&emsp; + Connect using MobaXterm <br>&emsp; + Create NAT Gateway <br>&emsp; + Monitor EC2 using CloudWatch <br>&emsp; + Troubleshoot connection using Reachability Analyzer                                   | 15/09/2025 | 15/09/2025      | <https://000003.awsstudygroup.com/> |
| 4   | - Learn and configure Hybrid DNS with Route 53 <br> - **Practice:** <br>&emsp; + Create Key Pair <br>&emsp; + Launch CloudFormation <br>&emsp; + Configure Security Group <br>&emsp; + Connect to RDGW using RDP protocol <br>&emsp; + Create Route 53 Inbound, Outbound <br>&emsp; + Create Route 53 Resolver Rules <br>&emsp; + Connect to RD Gateway Server to verify results                                                                        | 17/09/2025 | 17/09/2025      | <https://000010.awsstudygroup.com/> |
| 5   | - Learn and configure VPC Peering <br> - **Practice:** <br>&emsp; + CloudFormation <br>&emsp; + Create Security Group <br>&emsp; + Launch EC2 Instances <br>&emsp; + Ping between 2 EC2s <br>&emsp; + Update Network ACL <br>&emsp; + Create Peering Connection <br>&emsp; + Configure Route Table <br>&emsp; + Enable Cross-Peer DNS <br>&emsp; + Ping again between 2 EC2s                                                                            | 18/09/2025 | 18/09/2025      | <https://000019.awsstudygroup.com/> |
| 6   | - Learn about AWS Transit Gateway <br> - **Practice:** <br>&emsp; + Create Key Pair <br>&emsp; + Launch CloudFormation using template file <br>&emsp; + Create Transit Gateway <br>&emsp; + Create Transit Gateway Attachment for 4 VPCs with TG <br>&emsp; + Configure Route Table for Transit Gateway <br>&emsp; + Add Transit Gateway Routes to VPC Route Tables <br>&emsp; + Test Internet connectivity <br>&emsp; + Test connectivity between VPCs | 19/09/2025 | 19/09/2025      | <https://000020.awsstudygroup.com/> |

### Week 2 Achievements:

- Learned basic concepts of VPC:

  - VPC (Virtual Private Cloud): allows launching resources inside a virtual network that you create
  - The main purpose of VPC is to separate environments
  - A VPC can create multiple virtual networks and further divide them into sub-networks (Subnets)
  - A VPC exists within a Region, and VPC Subnets exist within a specific AZ
  - When a VPC is created → AWS automatically creates a Default Route Table → the Route Table is associated with subnets

- Learned about VPC Endpoint:

  - Allows resources inside a VPC to connect to supported AWS services (AWS PrivateLink) without requiring Internet access
  - There are 2 types of VPC Endpoints:
    - Interface Endpoint: uses an ENI inside the VPC with a Private IP address to connect to the service
    - Gateway Endpoint: uses the route table to route traffic to the supported service endpoint (S3 and DynamoDB)
  - To connect externally through a public subnet → use Internet Gateway
  - For private subnets → place a NAT Gateway in a public subnet to allow outbound access

- Deployed VPC, created Subnets, Internet Gateway, Route Table, Security Group
- Deployed EC2 Instances in Subnets

  - Tested connectivity, connected via SSH to Private EC2
  - EC2 connected to Endpoint
  - Built a public web + private services system similar to enterprise structure

- Deployed CloudWatch for VPC

- Configured Hybrid DNS with Route 53 Resolver:

  - Created Key Pair
  - Launched CloudFormation
  - Connected to RDGW using RDP (Remote Desktop Protocol)
  - Used AWS Directory Service to deploy Microsoft AD
  - Created Route 53 Resolver Rules
  - Tested results

- Connected VPCs using VPC Peering

  - VPC Peering Connection: a network connection between 2 VPCs allowing routing of traffic via IPv4 or IPv6

  - Network ACL (Network Access Control List): a security layer at the Subnet level that can block traffic before it reaches the Security Group

  - Cross-Peering DNS: a VPC Peering feature that allows resources inside one VPC to resolve DNS of resources inside another VPC

  - CloudFormation: a service that automates the creation, configuration, and management of AWS infrastructure using code, typically in YAML or JSON templates

- Practiced connecting multiple VPCs using Transit Gateway
  - Transit Gateway: a service that connects VPCs and on-premises networks through a centralized hub
  - Transit Gateway Attachment: enables the connection between TGW and a specific network (such as VPC or VPN)
