## HR Data Lake Solution on AWS

### Project Description
Implementation of a cloud-based data lake using AWS services to analyze factors influencing employee satisfaction and engagement within an HR department.

### Project Title
Design and Deployment of HR Data Lake Architecture using AWS

### Objective
The primary goal of this project was to analyze, design, and implement a data lake solution in AWS to address the business question provided by the HR operations team:  
**“What are the main factors impacting employee satisfaction and engagement?”**  
This project represents a scaled-down, functional version of the data lake solution that enables correlating employee sentiment with performance data, allowing better data-driven decisions.

### Business Question
What are the main factors impacting employee satisfaction and engagement?

### Dataset
The project utilized two main datasets provided by the HR operations team:

- **Employee Surveys**: Feedback from employees regarding their work experience, engagement, and satisfaction.
- **Performance Reviews**: Records of employee performance assessments conducted quarterly.

The datasets were provided in CSV and JSON formats with quarterly read/write frequency requirements.

### Methodology

#### 1. Analysis and Data Understanding
- Reviewed the business question and identified relevant datasets.
- Created a Fishbone Diagram to map potential causes of low employee satisfaction.

![project-1-fishbone](images/project-1-fishbone.jpg)

#### 2. Data Lake Design
- Standardized data formats into structured folders (CSV/JSON) within the data lake.
- Created an overall HR Data Lake architecture using AWS services.
- Designed the solution using:
  - AWS S3 for storage
  - EC2 for compute processing
  - EBS for storage
  - VPC for networking
  - Security Groups for access control

![project-1-datalake-design](images/project-1-datalake-design.jpg)

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

- AWS S3, EC2, VPC, Security Groups, EBS, Glacier Instant Retrieval
- AWS CLI for provisioning resources
- Data formats: CSV, JSON
- Draw.io for architecture and analysis diagrams

### Deliverables

- A functioning AWS HR Data Lake prototype ready for further expansion (VPC, EC2, S3, Lifecycle policies).
- Architecture design diagrams and fishbone analysis to frame the business problem.
- Initial report documenting design, implementation, and validation steps.

### Summary
This project demonstrates the implementation of a scalable AWS data lake to support HR data analytics, enabling data-driven decisions to improve employee engagement and satisfaction.
