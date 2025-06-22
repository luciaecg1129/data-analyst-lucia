## Lucia Ceron

## Project Description: AWS-Based HR Data Lake for Employee Satisfaction Analysis

### Project Title: Designing a Scalable HR Data Lake on AWS

### Objective
The primary goal of this project was to design, build, and implement a data lake solution on AWS to analyze factors impacting employee satisfaction and engagement. The system enables HR leadership to correlate employee sentiment with performance data to generate actionable insights.

### Dataset
The project utilized two main datasets provided by the HR operations team:

- **Employee Surveys**: Feedback from employees regarding their work experience, engagement, and satisfaction.
- **Performance Reviews**: Records of employee performance assessments conducted quarterly.

The datasets were provided in CSV and JSON formats, with quarterly read/write frequency requirements.

### Methodology

#### 1. Data Collection and Preparation
- Collected Employee Surveys and Performance Reviews data shared by the operations team.
- Standardized data formats into structured folders (CSV/JSON) within the data lake.

#### 2. Data Lake Design
- Created an overall HR Data Lake architecture using AWS services.
- Designed the solution using AWS S3 for storage, EC2 for compute processing, EBS for storage, VPC for networking, and Security Groups for access control.

#### 3. Implementation
- Provisioned a custom VPC and Security Group to allow controlled access.
- Launched a Windows EC2 instance (t3.micro) for data processing operations.
- Configured Amazon S3 buckets with structured folders for each dataset.
- Implemented lifecycle policies to automatically transition infrequently accessed data to Glacier Instant Retrieval for cost optimization.

#### 4. Cost Optimization
- Enabled S3 lifecycle rules based on quarterly access patterns, significantly reducing long-term storage costs.

#### 5. Deployment Testing
- Successfully verified account setup, VPC, EC2 instance deployment, storage configurations, and lifecycle policies using AWS console and CLI commands.

### Tools and Technologies
- **AWS Services**: S3, EC2, EBS, VPC, Security Groups, Glacier Instant Retrieval
- **AWS CLI** for infrastructure provisioning
- **Data formats**: CSV, JSON

### Deliverables
- A functioning AWS HR Data Lake prototype ready for further expansion.
- Architecture design diagrams and fishbone analysis to frame the business problem.
- Initial report documenting design, implementation, and validation steps.

> This project demonstrates the implementation of a scalable AWS data lake to support HR data analytics, enabling data-driven decisions to improve employee engagement and satisfaction.

---

## HR Data Ingestion and Cleaning using AWS Cloud

### Project Description
This project focuses on evaluating data ingestion costs and performing data cleaning on HR datasets using AWS Cloud services. The objective was to simulate real-world data management scenarios by leveraging cloud-native tools to optimize storage costs and ensure high data quality for analysis.

### Objective
- Estimate cloud storage costs for HR data ingestion.
- Identify and correct data structure and quality issues.
- Implement automated data cleaning pipelines.
- Prepare cleaned datasets for further analysis and decision-making.

### Datasets
- **Employee Surveys**: Collected feedback and responses from employees.
- **Performance Reviews**: Contained employee evaluations and performance metrics.

### Methodology

#### 1. Cost Evaluation of Data Ingestion
- Used **AWS Pricing Calculator** to estimate storage costs in Amazon S3 (Standard class).
- Parameters included:
  - Storage size estimation
  - Upload frequency (4 times/month)
  - Average object size
- Estimated cost:
  - $0.02 USD monthly
  - $6.01 USD annually

#### 2. Data Cleaning Analysis & Design
- Identified data issues such as:
  - Inconsistent schema (e.g., column name mismatches)
  - Duplicate records
- Designed cleaning workflows for both datasets individually.

#### 3. Data Cleaning Implementation
- Implemented using **AWS Glue DataBrew**:
  - Standardized column names and data types.
  - Removed duplicate rows.
- Created separate S3 buckets for raw and cleaned data ("raw zone" and "cleaning zone").
- Executed Glue jobs to automate the cleaning pipelines.
- Cleaned datasets were stored in a structured format, ready for downstream analytics.

#### 4. Cloud Features Utilized
- Seamless integration between AWS services (S3, Glue, DataBrew).
- Automation of data preparation tasks.
- Scalability to handle growing datasets.
- Simplified orchestration of complex data workflows.

### Tools and Technologies
- **AWS S3**: Cloud object storage
- **AWS Glue DataBrew**: Visual data preparation
- **AWS Pricing Calculator**: Cost estimation

### Deliverables
- Cost evaluation report for data ingestion.
- Automated data cleaning pipelines.
- Cleaned and structured HR datasets.
- Documentation and visual evidence of each implementation step.

### Key Takeaways
This project demonstrates how cloud-based data engineering simplifies complex data preparation processes while controlling costs. By leveraging AWS-native tools, the solution achieved automation, scalability, and operational efficiency, preparing high-quality HR data for future analytics and decision-making.

---

## Project Title: Employee Satisfaction and Performance Analysis using AWS Services

### Project Description
The project aimed to analyze employee satisfaction and performance metrics by designing and implementing a data analytics pipeline within the AWS ecosystem. This involved transforming raw HR datasets into a reliable **Single Source of Truth (SST)** to support descriptive, diagnostic, and prescriptive analysis aligned with business objectives.

### Objective
The main objective was to process and analyze employee surveys and performance datasets to answer business questions related to:
- Average satisfaction by quarter
- Employee engagement levels
- Performance evaluations

Through this analysis, actionable insights were derived to support HR decision-making.

### Dataset
The project utilized two primary datasets:
- **Employee Surveys**: Containing satisfaction scores, engagement responses, and survey dates.
- **Performance Reviews**: Containing evaluation scores, assessment periods, and related performance metrics.

Key dataset features:
- EmployeeID (used for joining datasets)
- Satisfaction scores
- Engagement levels
- Evaluation statuses
- Dates of surveys and assessments

### Methodology

#### Data Collection and Preparation
- Loaded datasets into AWS S3.
- Used AWS Glue DataBrew to perform data profiling, cleaning, and resolving datatype inconsistencies.
- Combined datasets via inner join on EmployeeID.

#### ETL Design and Implementation
- Designed ETL flows using AWS Glue Studio with SQL-based transformations.
- Saved transformed data into AWS S3 in Parquet format for optimized storage and querying.
- Registered the transformed datasets into AWS Glue Data Catalog.
- Enabled querying via Amazon Athena for flexible data analysis.

#### Cost Monitoring
- Used AWS Pricing Calculator for cost estimation.
- Configured AWS CloudWatch alarms to monitor estimated costs and maintain budget control.

#### Analysis and Metrics Generation
- Generated descriptive statistics such as:
  - Average satisfaction by quarter
  - Employee engagement levels
  - Correlation between performance evaluations and satisfaction scores

### Tools and Technologies
- **AWS Glue** (Glue Studio, DataBrew, Data Catalog)
- **Amazon S3**
- **Amazon Athena**
- **AWS CloudWatch**
- **AWS Pricing Calculator**
- **SQL**

### Deliverables
- A fully automated ETL pipeline for HR data.
- Clean, enriched, and queryable datasets available through Athena.
- Cost-effective architecture with continuous monitoring.
- Key metrics and insights supporting HR strategic decisions.

---

## Project Description: AWS Data Analytics Platform for the City of Vancouver

### Project Title: Designing and Implementing a Data Analytics Platform for Cultural Spaces in Vancouver

### Objective:
The goal of this project was to design, build, and deploy a scalable Data Analytics Platform (DAP) on AWS for the City of Vancouver. The platform supports descriptive analysis to help city officials analyze trends in cultural space usage, ownership, and growth patterns in the downtown area.

### Dataset:
The dataset used in this project was obtained from the City of Vancouver Open Data Portal, focusing on cultural spaces from 2014 to 2020. Key features include:
- Cultural Space Name
- Type (e.g., Cafe/Restaurant/Bar, Museum, Education, etc.)
- Primary Cultural Use
- Square Footage
- Ownership Type (Private, Non-Profit, Government)
- Year of Data Collection
- Geographic Coordinates

### Methodology:

#### 1. Data Ingestion:
- Downloaded the dataset in CSV format.
- Uploaded raw data to Amazon S3 with organized folder structure to allow scalability for future datasets.
- S3 Bucket: `cs-raw-luc` following path `cs/Cultural_Spaces/year=20/CSV/`

#### 2. Data Profiling:
- Used AWS Glue DataBrew to profile data.
- Identified issues such as missing values (e.g., 38% missing in 'square feet', 80% missing in 'number of seats').
- Reviewed data quality before proceeding to cleaning phase.

#### 3. Data Cleaning:
- Used AWS Glue DataBrew to create cleaning recipes.
- Actions included: correcting text inconsistencies, removing irrelevant columns, and deleting rows with missing critical values.
- Cleaned data stored in S3 Bucket: `cs-cln-luc`.

#### 4. Data Cataloging:
- Used AWS Glue Data Catalog to create metadata tables.
- Implemented crawlers to automatically extract schema from cleaned data.
- Enriched data using ETL pipelines by adding fields like processing timestamps.
- Curated data stored in S3 Bucket: `cs-cur-luc`.

#### 5. Data Summarization:
- Used Amazon Athena to run SQL queries for descriptive analysis.
- Metrics calculated:
  - Average Square Footage by Ownership Type (`avg_sqft_by_ownership`)
  - Count of Cultural Spaces by Type (`num_cultural_spaces_by_type`)
- Analyzed trends showing increasing private ownership and growth of specific cultural types.

### Tools and Technologies:
- AWS S3 (Storage)
- AWS Glue (DataBrew, Data Catalog, ETL Pipeline)
- Amazon Athena (Query Engine)
- SQL (for data summarization)

### Deliverables:
- Fully functional AWS Data Analytics Platform.
- Cleaned, cataloged, and query-ready dataset.
- Descriptive analysis reports with trend insights.
- SQL scripts and documented ETL processes.

### Insights and Findings:
- Private ownership of cultural spaces in downtown Vancouver increased significantly between 2014 and 2020.
- Certain cultural space types like Cafe/Restaurant/Bar showed consistent growth while others like Museums experienced decline.

This project demonstrates end-to-end implementation of a cloud-based data analytics pipeline using AWS services, enabling public sector data-driven decision making.
---

## AWS Data Analytics Platform for City of Vancouver

### Project Description
This project involved the design and deployment of a comprehensive Data Analytics Platform (DAP) on AWS to support the City of Vancouver's data processing, governance, security, and monitoring requirements. The solution utilizes multiple AWS services to provide secure, reliable, and scalable data analytics capabilities.

### Project Title
AWS-Based Data Analytics Platform Migration for City of Vancouver

### Objective
The main objective was to architect and implement a secure and fully managed AWS data analytics solution that enables the City of Vancouver to efficiently ingest, process, govern, monitor, and store cultural spaces datasets, while ensuring data security, quality, compliance, and cost optimization.

### Dataset
The dataset focused on cultural spaces and included the following key fields:
- `cultural_space_name`: Name of the cultural space
- `year`: Year of data entry
- `type`: Type of cultural space
- `primary_use`: Main purpose of the space

### Methodology

#### 1. Data Security
- **Encryption**: Implemented server-side encryption using AWS KMS with customer-managed keys (CMKs) to maintain full control over encryption keys.
- **Versioning**: Enabled S3 bucket versioning to support data recovery and retention.
- **Replication**: Configured S3 cross-region replication (CRR) to replicate data from primary buckets to backup buckets for disaster recovery:
  - `cs-raw-luc` → `cs-raw-bac-luc`
  - `cs-cln-luc` → `cs-cln-bac-luc`
  - `cs-cur-luc` → `cs-cur-bac-luc`

#### 2. Data Governance
- **ETL Pipelines**: Developed visual ETL pipelines using AWS Glue Studio.
- **Data Quality Evaluation**: Implemented data quality rules using `Evaluate Data Quality` nodes with conditions:
  - Completeness: 
    - `cultural_space_name` ≥ 90%
    - `year` > 99%
    - `type` ≥ 95%
    - `primary_use` > 99%
  - Uniqueness:
    - `cultural_space_name` ≥ 80%
- **Routing Results**: Automatically routed valid records to `cs-cln-luc/Quality_Check/Passed` and invalid records to `cs-cln-luc/Quality_Check/Failed`.

#### 3. Data Monitoring
- **CloudWatch Dashboards**: Created custom dashboards to monitor:
  - S3 bucket size growth
  - Glue ETL job performance
  - AWS billing and usage metrics
- **CloudWatch Alarms**: Configured alarms to send email notifications on:
  - High AWS estimated charges
  - Resource usage thresholds
- **CloudTrail Auditing**: Enabled AWS CloudTrail for auditing user and system activities across the platform, improving traceability and troubleshooting capabilities.

#### 4. Architecture Evaluation (Well-Architected Framework)
- **Operational Excellence**: Automation via ETL pipelines and dashboards
- **Security**: Customer-managed encryption keys and full audit trails
- **Reliability**: Backup replication and versioning strategies
- **Performance Efficiency**: Serverless ETL with Glue; scalable object storage with S3
- **Cost Optimization**: Monitored with proactive billing alerts and usage dashboards

### Tools and Technologies
- **AWS S3** (Object Storage, Versioning, Replication)
- **AWS KMS** (Key Management Service for encryption)
- **AWS Glue** (ETL, Data Quality Checks)
- **AWS CloudWatch** (Dashboards, Alarms, Metrics)
- **AWS CloudTrail** (Logging & Auditing)
- **AWS IAM** (Access Management - with fine-grained permissions)

### Deliverables
- Fully functional AWS data analytics platform for ingestion, transformation, and storage
- Automated ETL pipelines with data quality controls
- Secure storage with encryption, versioning, and cross-region replication
- Real-time monitoring dashboards and proactive alerting
- Comprehensive audit logs for compliance and incident response

This project showcases a full-scale AWS cloud data analytics deployment for a public sector client, leveraging multiple AWS services to address real-world data management challenges.

