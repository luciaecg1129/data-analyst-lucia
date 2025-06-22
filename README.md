## Lucia Ceron
Below is a **ready-to-paste README section** that follows your professor’s preferred template and adds the technical depth a recruiter or reviewer will expect.
All headings start at level 2 (`##`) so they slot cleanly into a larger GitHub page.

---
## Project Description: Scalable HR Data Lake on AWS

### Project Title: Designing a Scalable HR Data Lake on AWS

**Objective**
Design and deploy a secure, cost-efficient data-lake architecture that lets HR leadership correlate quarterly **Employee Surveys** with **Performance Reviews**, generating insight into satisfaction vs. performance trends.

**Dataset**
*Format & cadence – CSV / JSON, quarterly reads & writes*

| Key Feature                            | Description                                    |
| -------------------------------------- | ---------------------------------------------- |
| `EmployeeID`                           | Unique identifier enabling cross-dataset joins |
| `SurveyDate`, `ReviewPeriod`           | Timestamps for sentiment vs. performance       |
| `SatisfactionScore`, `EngagementLevel` | Self-reported HR sentiment metrics             |
| `PerformanceRating`, `GoalsMet`        | Supervisor-assigned review metrics             |

**Methodology**

1. **Data Collection & Preparation**

   * Imported raw CSV/JSON files from HR SharePoint → landing S3 bucket (`hr-raw/`); validated file integrity with `aws s3api head-object`.
2. **Data-Lake Design**

   * Crafted three-zone S3 layout (`raw`, `curated`, `archive`); folder naming uses `<dataset>/<year>/` partitioning for Athena predicate pushdown.
   * Selected **t3.micro Windows EC2** for ad-hoc processing and container registry sync.
3. **Implementation**

   * Deployed custom **/24 VPC**, one public and two private subnets; attached **Security Group** permitting 443/22 only from HQ CIDR.
   * Mounted 20 GB **gp3 EBS** volume to EC2; installed AWS CLI v2 and SSM agent for session-manager access (no exposed SSH key).
4. **Cost Optimization**

   * **Lifecycle Rule:** after 90 days → *Glacier Instant Retrieval*; after 365 days → *Glacier Deep Archive*.
   * Tagged all S3 objects with `CostCenter=HR-Analytics` for Cost Explorer filtering.
5. **Validation & Handoff**

   * Smoke-tested IAM least-privilege roles (`HRDLake-EC2Role`, `HRDLake-LambdaRole`).
   * Produced Visio architecture diagram + fishbone root-cause model.

**Tools & Technologies**
AWS S3 · EC2 · EBS · VPC · Security Groups · Glacier IR/DA · AWS CLI

**Deliverables**

* Architecture & security diagrams (PNG)
* Terraform scripts & user-data bash bootstrap
* Step-by-step validation report (Markdown with CLI outputs)

---

## Project Description: HR Data Ingestion & Cleaning on AWS

### Project Title: Automating Data Ingestion and Cleaning for HR Analytics

**Objective**
Estimate ingestion costs and implement repeatable, serverless data-cleaning pipelines that deliver analytics-ready HR datasets.

**Dataset**
See previous project for schema details; \~50 MB monthly combined size.

**Methodology**

1. **Cost Evaluation**

   * Built scenario in **AWS Pricing Calculator**: 200 MB/mo writes, Standard class, 4 PUTs per mo → **\$0.02 USD/mo** (\~\$6.01/yr).
2. **Schema & Quality Profiling**

   * Ran **Glue DataBrew** profiling job → flagged 3 % missing `EngagementLevel`, 2 duplicate `EmployeeID` rows.
3. **Cleaning Pipeline**

   * DataBrew recipe: rename snake-case columns, cast dates to ISO 8601, remove duplicates.
   * Job output to `s3://hr-clean/` (*clean zone*) in compressed Parquet.
4. **Automation & Logging**

   * Trigger: EventBridge rule on object-created (`hr-raw/`) → DataBrew job run; logs to CloudWatch `/${AWS::StackName}/DataBrew`.

**Tools & Technologies**
AWS S3 · Glue DataBrew · EventBridge · CloudWatch Logs · Pricing Calculator

**Deliverables**

* Calculator cost sheet (PDF)
* DataBrew recipe JSON + job run screenshots
* Clean-data manifest & Glue catalog table

---

## Project Description: Employee Satisfaction & Performance Analysis Pipeline

### Project Title: Building a Single Source of Truth for HR Metrics

**Objective**
Transform raw HR datasets into a curated Parquet lakehouse, expose KPIs (average satisfaction per quarter, engagement vs. rating correlations) through SQL-on-S3.

**Dataset**
Same as above, but enriched with derived flags (`IsHighPerformer`, `TenureBand`).

**Methodology**

1. **ETL Design (Glue Studio)**

   * Node graph: *S3 Source* → *Join* on `EmployeeID` → *Transform* (SQL) → *S3 Target*.
   * Saved as hourly trigger job; output partitioned by `year`, `quarter`.
2. **Catalog & Query**

   * Automatic crawler registers Parquet schema to **Glue Data Catalog**.
   * **Amazon Athena** views expose KPIs; sample query:

     ```sql
     SELECT quarter, AVG(satisfactionscore) AS avg_sat
     FROM hr_curated
     GROUP BY quarter ORDER BY quarter;
     ```
3. **Cost & Ops**

   * **CloudWatch Alarms** for estimated charges > \$5 (SNS e-mail).
   * Enabled Athena workgroup encryption (KMS CMK) & saved query outputs to `athena-results/`.

**Tools & Technologies**
AWS Glue Studio · Glue Catalog · S3 (Parquet) · Athena · CloudWatch · KMS

**Deliverables**

* ETL job JSON + screenshots
* Athena DDL & sample query notebook
* Metrics slide deck with charts (PNG exported from QuickSight)

---

## Project Description: Cultural-Spaces Analytics Platform (City of Vancouver)

### Project Title: Designing & Implementing a Data Analytics Platform for Cultural Spaces

**Objective**
Provide city planners with descriptive analytics on cultural-space growth, ownership shifts, and usage patterns (2014-2020).

**Dataset**

| Field                 | Description                       |
| --------------------- | --------------------------------- |
| `cultural_space_name` | Venue name                        |
| `type`                | Café, Museum, Education, etc.     |
| `primary_use`         | Main cultural purpose             |
| `square_footage`      | Gross floor area                  |
| `ownership_type`      | Private / Non-Profit / Government |
| `year`                | Data-collection year              |
| `lat`, `lon`          | Coordinates                       |

**Methodology**

1. **Ingestion & Zoning**

   * Raw CSV → `cs-raw-luc/`; profiled with DataBrew.
2. **Cleaning**

   * Filled 38 % missing `square_footage` with median per `type`; dropped rows missing both area & seats.
3. **Cataloging & Enrichment**

   * Glue crawler creates `cultural_spaces_raw` & `cultural_spaces_cln` tables.
   * ETL adds `ingest_timestamp`, normalizes `type` text.
4. **Descriptive Analytics (Athena)**

   * KPIs: `avg_sqft_by_ownership`, `num_spaces_by_type`.
   * Discovered 2× growth in privately owned spaces between 2014-2020.

**Tools & Technologies**
AWS S3 · Glue DataBrew · Glue ETL · Glue Catalog · Athena

**Deliverables**

* Clean & curated S3 buckets
* SQL notebook with trend visualizations
* Findings report for city cultural-affairs team

---

## Project Description: AWS-Based Analytics Platform Migration for City of Vancouver

### Project Title: Secure, Governed, and Monitored Data Analytics Platform

**Objective**
Harden the cultural-spaces pipeline with encryption, data-quality rules, cross-region DR, and full monitoring per AWS Well-Architected Framework.

**Dataset**
Curated cultural-spaces dataset from previous project.

**Methodology**

1. **Data Security**

   * Enabled **S3 Versioning** and **CRR** (`*-bac-luc` buckets).
   * Server-side encryption (SSE-KMS) using **customer-managed CMK**.
2. **Governance & Quality**

   * **Glue Studio** ETL with *Evaluate Data Quality* nodes:

     * Completeness: `cultural_space_name` ≥ 90 %, `type` ≥ 95 %, `primary_use` ≥ 99 %
     * Uniqueness: `cultural_space_name` ≥ 80 %
   * Pass/fail routing to dedicated prefixes.
3. **Monitoring & Logging**

   * **CloudWatch Dashboards**: S3 growth, Glue job DPU time, estimated charges.
   * **CloudWatch Alarms**: spend > \$10, DPU time > 15 min/job.
   * **CloudTrail** enabled for account-wide API auditing.
4. **Architecture Review**

   * Aligned with Well-Architected pillars: Operational Excellence, Security, Reliability, Performance, Cost.

**Tools & Technologies**
AWS S3 · KMS · Glue Studio · Glue Data Quality · CloudWatch · CloudTrail · IAM

**Deliverables**

* Updated architecture diagram with DR arrows
* Data-quality rule config JSON
* CloudWatch dashboard & alarm screenshots
* Compliance/audit workbook (Markdown)


