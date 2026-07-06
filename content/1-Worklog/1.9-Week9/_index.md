---
title: "Week 9 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.9. </b> "
---
This week's internship tasks focused on designing the system deployment architecture on AWS, completing the design documentation, and preparing all necessary resources for the actual production deployment of the **EAM Workspace** project.

### Week 9 Objectives:
* Design the deployment architecture for the system on AWS.
* Complete the architectural design documentation.
* Prepare for production deployment.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| **Fri** | - Analyze deployment requirements for the **EAM Workspace** project.<br>- Draft the overall AWS Architecture Diagram for the system.<br>+ Prepare related design documentation. | 12/06/2026 | 12/06/2026 | Project source code, Team discussion |
| **Sat** | - Design the detailed user access path.<br>- Analyze traffic routing through the Frontend (AWS Amplify), Application Load Balancer, Elastic Beanstalk, and Amazon RDS.<br>+ Document packet routing and data connections. | 13/06/2026 | 13/06/2026 | Project source code, Team discussion |
| **Sun** | - Design the logical network infrastructure model for the system.<br>- Segment the network layout consisting of a VPC, Public Subnets (for ELB, NAT), Private Subnets (for app, DB), Internet Gateway, and NAT Gateway.<br>+ Ensure appropriate security and network isolation. | 14/06/2026 | 14/06/2026 | Project source code, Team discussion |
| **Mon** | - Design the integration of object storage and email notification services.<br>- Incorporate Amazon S3 and Amazon SES into the infrastructure design.<br>+ Plan configuration details and source code integration. | 15/06/2026 | 15/06/2026 | Project source code, Team discussion |
| **Tue** | - Design and add solutions for log monitoring, audit trails, and secure configurations.<br>- Integrate CloudWatch Logs, CloudTrail, Secrets Manager, and Parameter Store.<br>+ Establish standards for managing secure environment variables. | 16/06/2026 | 16/06/2026 | Project source code, Team discussion |
| **Wed** | - Review the entire designed network and system infrastructure architecture.<br>- Evaluate Scalability, High Availability, and information security.<br>+ Revise suboptimal areas in technical drawings. | 17/06/2026 | 17/06/2026 | Project source code, Team discussion |
| **Thu** | - Finalize deployment architecture diagrams and descriptions.<br>- Assess and prepare resources required for actual infrastructure deployment.<br>+ Plan tasks for the next week. | 18/06/2026 | 18/06/2026 | Project source code, Team discussion |

### Week 9 Achievements:
* Completed the AWS deployment architecture diagram (AWS Architecture Diagram) for the **EAM Workspace** system.
* Finalized the network model and application deployment flow.
* Identified all AWS services required for the project, including: AWS Amplify, Elastic Beanstalk, Application Load Balancer, Amazon RDS, Amazon S3, Amazon SES, CloudWatch, CloudTrail, Secrets Manager, and Parameter Store.

### Plan for the Next Week:
* Start deploying the network infrastructure (VPC, Subnets, Route Tables, IGW, NAT Gateway) on AWS.
* Set up related AWS services and prepare environment for application deployment.
* Perform test deployments of Frontend and Backend components on the actual AWS environment.
