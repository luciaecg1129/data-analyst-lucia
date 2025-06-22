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


