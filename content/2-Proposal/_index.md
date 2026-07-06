---
title: "Proposal"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# Proposal: Deploying an Enterprise Asset Management System
## Cloud Workspace for Enterprise Asset Management

### 1. Executive Summary
The project aims to build EAM Workspace, a web-based enterprise asset management system deployed on AWS. The system targets the challenge of office asset management within enterprises, where information about equipment, users, assignments, maintenance, and inventory needs to be tracked clearly, centrally, and easily retrieved.

EAM Workspace supports enterprises in managing employees, departments, assets, assignments, maintenance requests, inventory sessions, reports, feedback, FAQ, attendance, login history, notifications, and support chat in a centralized workspace. Instead of storing disjointed information using Excel, messages, or local files, the system consolidates key business workflows into a single application with clear role-based access control for administrators and employees.

The system was developed by a team of 5 members. The project includes a React frontend, Node.js/Express backend, MySQL database managed by Prisma, and a deployment plan on AWS. Within the scope of this report, the content focuses on UI building, API integration, AWS services research, full-stack demo deployment, and workshop documentation during the internship from April 17, 2026 to July 10, 2026.

In the demo version, the AWS architecture utilizes AWS Amplify Hosting for the frontend, Amazon API Gateway as the public API layer, AWS Elastic Beanstalk for the Node.js backend, Amazon RDS for MySQL for business data, Amazon SES for sending emails, and Amazon CloudWatch for logging/monitoring. Services such as Amazon S3, AWS Secrets Manager, AWS Systems Manager Parameter Store, and AWS CloudTrail are included as expansion guidelines to prepare the system for a production environment.

---

### 2. Intended System Use
EAM Workspace is designed to assist enterprises in managing the entire asset lifecycle from creation, categorization, assignment to employees, maintenance logging, inventory tracking, recovery, to usage reports. The system is suitable for businesses with numerous office equipment units (laptops, monitors, printers, peripherals) or assets that require tracking by department and user.

For administrators, the system helps track the asset list, asset status, current users, assignment history, maintenance requests, inventory data, and general reports. For employees, the system provides a self-service portal to view assigned assets, submit support requests, view personal profiles, and track activities related to their assets.

The primary goal of the project is not only to build a web application with full asset management capabilities, but also to practice deploying a full-stack system on AWS, configuring frontend-backend-database connections, testing in a public environment, and managing post-deployment costs.

---

### 3. Problem Statement
#### Current Issues
Many small and medium-sized enterprises still manage office assets using spreadsheets, messages, or scattered internal files. This approach leads to several problems:
* Scattered asset information that is difficult to update.
* Administrators struggle to track who is using which asset.
* Assignment, recovery, transfer, maintenance, and inventory history is difficult to trace.
* Employees lack a clear self-service portal to view assigned assets or submit support requests.
* Report generation is slow because data must be gathered and processed manually.
* File attachments, asset images, and feedback are difficult to organize centrally.

#### Proposed Solution
EAM Workspace solves these issues by providing a centralized web application with two main portals:
* **Admin Portal**: for administrators to manage employees, departments, asset categories, assets, assignments, maintenance requests, inventory sessions, locations, reports, feedback, FAQ, attendance history, login history, and support chat.
* **Employee Portal**: for employees to view assigned assets, see asset details, submit support requests, view FAQ, update profiles, change passwords, view personal history, and chat for support.

The application is deployed on AWS so that the frontend, backend, database, and supporting services can run in a cloud environment, making them easier to access, monitor, and scale. During the internship, self-study of AWS was conducted alongside product development, focusing on AWS accounts, IAM, networking, compute, database, storage, deployment, monitoring, and cost optimization.

#### Benefits
* Centralized management of the asset lifecycle from creation, assignment, maintenance, and inventory to reporting.
* Clear separation of administrator and employee workflows.
* Enhanced security through authentication, role-based access control, private database configurations, and environment variable control.
* Easy to demo and deploy using AWS managed services.
* Clear upgrade roadmap from an internal demo environment to a production environment.

---

### 4. Solution Architecture
The proposed AWS deployment architecture follows a simple full-stack web application model for an internal demo environment. The current deployment mode does not require Route 53 or custom domains. Users access the default AWS Amplify Hosting URL, and API requests from the frontend are rewritten via `/api/*` to Amazon API Gateway. API Gateway forwards these requests to the backend running on AWS Elastic Beanstalk, which connects to Amazon RDS for MySQL.

#### AWS Services Used
* **AWS Amplify Hosting**: Hosts and builds the React frontend from the deployment branch.
* **Amazon API Gateway HTTP API**: Ingests `/api/*` requests from Amplify and forwards them to the backend.
* **AWS Elastic Beanstalk**: Runs the Node.js/Express backend with deployment processes managed by AWS.
* **Amazon EC2**: Provides compute instances managed by Elastic Beanstalk.
* **Amazon RDS for MySQL**: Stores data such as users, employees, departments, assets, assignments, maintenance requests, inventory sessions, and reports.
* **Amazon S3**: Stores asset images and uploaded files in the expanded design for production.
* **Amazon SES**: Sends OTPs and application emails.
* **AWS Secrets Manager**: Intended to store sensitive values like application secrets or database credentials when upgrading from the demo mode.
* **AWS Systems Manager Parameter Store**: Intended to store runtime configuration values.
* **Amazon CloudWatch Logs and Alarms**: Collects backend logs and supports monitoring.
* **AWS CloudTrail**: Intended to log activities within the AWS account for auditing purposes.
* **AWS Systems Manager Session Manager**: Intended to support secure instance management without opening public SSH ports.

#### Application Components
* **Frontend**: React, Vite, Tailwind CSS, React Router, reusable UI components, Admin Portal, and Employee Portal.
* **Backend**: Node.js, Express.js, Prisma ORM, JWT authentication, validation, centralized error handling, request logging, and REST API modules.
* **Database**: MySQL schema for users, employees, departments, assets, assignments, maintenance requests, inventory sessions, notifications, feedback, attendance, login history, and support chat.
* **Deployment**: AWS Amplify for frontend hosting, API Gateway for the API entry point, Elastic Beanstalk for backend hosting, RDS for the database, and CloudWatch for logs.

---

### 5. Technical Implementation Plan
* **Phase 1: Requirement Analysis and UI Planning**
  * Analyze the asset management problem and define main modules.
  * Identify the two user groups: administrators and employees.
  * Design core workflows for asset creation, assignment, recovery, maintenance, inventory, reporting, and employee self-service.
  * Build reusable UI templates for the Admin Portal.
  * Self-study AWS fundamentals: accounts, cost management, IAM, Regions/AZs, and basic cloud concepts.

* **Phase 2: Backend and Database Foundation**
  * Design the MySQL schema using Prisma.
  * Implement authentication, authorization, account status verification, and password handling.
  * Build REST APIs for employees, departments, categories, assets, assignments, maintenance requests, inventory, reports, notifications, feedback, FAQ, attendance, login history, and support chat.
  * Populate seed data for demo accounts and sample business data.

* **Phase 3: Frontend Development**
  * Build Admin Portal screens for asset and organization management.
  * Build Employee Portal screens for self-service workflows.
  * Integrate APIs with the backend.
  * Implement loading, empty, error, and toast states.
  * Review responsive behavior and dark/light modes.
  * Self-study AWS services related to compute, storage, database, networking, and deployment to prepare for the deployment phase.

* **Phase 4: AWS Deployment**
  * Create or use Amazon RDS for MySQL for the application database.
  * Configure security groups to allow backend access to RDS via port 3306.
  * Deploy backend on AWS Elastic Beanstalk, creating a source bundle suitable for Linux environments.
  * Configure environment variables such as `DATABASE_URL`, `JWT_SECRET`, `PORT`, `FRONTEND_ORIGIN`, and mail settings.
  * Run Prisma migrations and seed data if necessary.
  * Deploy frontend on AWS Amplify Hosting.
  * Configure Amazon API Gateway HTTP API to proxy requests to the Elastic Beanstalk backend.
  * Configure Amplify rewrite rules from `/api/*` to the API Gateway endpoint and SPA fallback to `index.html`.

* **Phase 5: Testing and Validation**
  * Test `GET /api/health`.
  * Verify admin and employee logins.
  * Test core CRUD workflows.
  * Test asset assignment, recovery, maintenance requests, inventory, and reporting.
  * Check CloudWatch Logs to detect backend errors.
  * Confirm that CORS, API Gateway routes/stages/integrations, and Amplify rewrite rules work correctly.
  * Verify image/avatar uploads, inactive account states, and core demo flows.

---

### 6. Timeline and Milestones

| Timeline | Milestones | Expected Outcomes |
| --- | --- | --- |
| **Week 1** | Project Orientation & AWS Foundations | Define frontend roles, set up environments, and learn basic AWS concepts. |
| **Week 2** | Initialize React App & Admin Layout | Build route structures, sidebar, layout, and basic components. |
| **Week 3** | Login, Token & API Layer | Complete protected routes, token handling, and service layers for backend integration. |
| **Week 4** | Basic Admin CRUD | Complete screens for assets, employees, departments, and main forms/tables. |
| **Week 5** | Asset Workflows | Develop asset assignment, recovery, transfer, and maintenance workflows. |
| **Week 6** | Inventory, Reporting & Data | Complete inventory, reports, charts, and data states. |
| **Week 7** | Refining UI Experience | Upgrade responsive layout, dark mode, loading/toast indicators, and UI error handling. |
| **Week 8** | User Portal & Expanded Modules | Complete employee dashboard, assigned assets, FAQ, feedback, Excel import, and floor map. |
| **Week 9** | AWS Deployment Preparation | Review production builds, environment configurations, deployment documentation, and integration fixes. |
| **Week 10** | AWS Deployment | Deploy with RDS, Elastic Beanstalk, API Gateway, and Amplify; test health endpoint and login flows. |
| **Week 11** | Production Testing & Workshop Docs | Fix integration bugs, check main screens, take workshop screenshots, and add deployment guides. |
| **Week 12** | Completing Final Report | Review Hugo site, complete self-evaluation, sharing/feedback, clean up resources, and prepare for report submission. |

---

### 7. Budget Estimation
The project is designed for an internal demo environment, prioritizing low cost over high availability for the initial deployment. The final costs should be verified using the AWS Pricing Calculator before deployment, as AWS pricing varies by Region, instance type, storage capacity, and traffic.

| Service | Cost Optimization Choice |
| --- | --- |
| **AWS Amplify Hosting** | Use the default Amplify domain and deploy only the required branch. |
| **Amazon API Gateway** | Use a simple HTTP API for the `/api/*` route. |
| **AWS Elastic Beanstalk / EC2** | Use a small instance class for the demo environment. |
| **Amazon RDS for MySQL** | Use Single-AZ and a small instance class for dev/test. |
| **Amazon S3** | Store only necessary uploaded files and apply clean-up policies if needed. |
| **Amazon SES** | Use only for application OTP and email flows. |
| **CloudWatch** | Limit log retention duration for the demo environment. |

#### Cost Control Actions:
* Use a single AWS Region for all resources.
* Do not enable RDS Multi-AZ during the demo phase.
* Do not use Route 53 or custom domains until production is required.
* Clean up Elastic Beanstalk, API Gateway, RDS, S3, and CloudWatch after the workshop.
* Do not keep unused deployment environments.

---

### 8. Risk Assessment

| Risk | Impact | Probability | Mitigation Strategy |
| --- | --- | --- | --- |
| **Incorrect Amplify rewrite rules** | Frontend fails to call backend API or static assets encounter MIME type errors | Medium | Place the `/api/*` rule above the SPA fallback, ensure static assets are not incorrectly rewritten, and test `/api/health`. |
| **Incorrect API Gateway routes or stages** | API returns 404 even when backend is running | Medium | Check routes, integrations, stages, and parameter mapping before testing the frontend. |
| **Incorrect Elastic Beanstalk port** | Backend becomes unhealthy | Medium | Set `PORT=8080` and ensure the backend reads the port from environment variables. |
| **Incorrect RDS security group configuration** | Backend cannot connect to MySQL | Medium | Open port 3306 only from the backend security group. |
| **CORS Errors** | Browser blocks API calls | Medium | Set `FRONTEND_ORIGIN` or `FRONTEND_ORIGINS` to the correct Amplify URL. |
| **Missing/incorrect production environment variables** | Login, upload, or health checks fail | Medium | Standardize `DATABASE_URL`, `JWT_SECRET`, `FRONTEND_ORIGIN`, and OTP/mail config; test each layer after deployment. |
| **Unstable file uploads** | Uploaded files are lost when instances are replaced | Medium | Use a private S3 bucket for production-ready storage or state the local upload limit clearly in the demo. |
| **Unexpected cost overheads** | Unnecessary AWS costs incurred | Low to Medium | Use the smallest instance resources for the demo, set budget alerts, and clean up resources post-testing. |
| **Lack of test data** | Cannot demonstrate core workflows | Medium | Run Prisma seeds before the demo and document demo accounts separately. |

---

### 9. Expected Outcomes
Upon completing the project and workshop, the expected outcomes include:
* A working Enterprise Asset Management application with Admin and Employee Portals.
* Backend APIs supporting authentication, authorization, asset lifecycle workflows, reporting, notifications, feedback, attendance, and support chat.
* A MySQL schema storing the core business data of the system.
* A practical AWS deployment model utilizing Amplify, API Gateway, Elastic Beanstalk, RDS, SES, and CloudWatch, along with design guidelines for S3, Secrets Manager, and Parameter Store.
* A step-by-step workshop allowing other learners to follow, deploy, and test the system.
* Improved understanding of full-stack deployment, cloud networking, environment variables, CORS, database connectivity, monitoring, and resource clean-up on AWS.

---

### 10. Future Work
* Migrate all file uploads from local instance storage to Amazon S3.
* Add Route 53 and AWS Certificate Manager when a custom production domain is required.
* Enable RDS Multi-AZ to increase availability.
* Add Auto Scaling for the backend as traffic increases.
* Add Amazon ElastiCache for Redis if the application requires shared state across multiple backend instances.
* Add AWS WAF when the application becomes public-facing.
* Improve CI/CD pipelines and automated testing for both frontend and backend.