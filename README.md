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
