---
title: "Week 3 Worklog"
date: 2026-06-15
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Week 3 Objectives:

* Build skills in data analytics and business intelligence on AWS
* Master serverless analytics with Amazon Athena
* Understand AWS Glue for ETL and data cataloging
* Create visual dashboards with Amazon QuickSight
* Explore PostgreSQL on AWS (Advanced)

### Tasks Carried Out This Week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ---- | ---------- | --------------- | ------------------ |
| 1 | **Data Analytics Services Overview:** <br>&emsp; + Compare AWS analytics services (Athena, Glue, EMR, Redshift, QuickSight) <br>&emsp; + Understand use cases for each | 15/06/2026 | 15/06/2026 | Analytics Module |
| 2 | **Serverless Analytics with Amazon Athena:** <br>&emsp; + Create Athena tables from S3 data <br>&emsp; + Write SQL queries on CSV/Parquet/JSON <br>&emsp; + Partition data for performance optimization | 16/06/2026 | 16/06/2026 | Athena Workshop |
| 3 | **AWS Glue:** <br>&emsp; + Crawlers and Data Catalog <br>&emsp; + ETL jobs using PySpark/Spark <br>&emsp; + Job bookmarks and scheduling | 17/06/2026 | 17/06/2026 | Glue Documentation |
| 4 | **Business Intelligence with Amazon QuickSight:** <br>&emsp; + Connect to Athena and S3 data sources <br>&emsp; + Build visualizations and dashboards <br>&emsp; + Share insights with stakeholders | 18/06/2026 | 18/06/2026 | QuickSight Workshop |
| 5 | **Advanced PostgreSQL on AWS - Part 1:** <br>&emsp; + Managed PostgreSQL with Amazon RDS <br>&emsp; + Performance tuning and monitoring <br>&emsp; + Read replicas and Multi-AZ deployment | 19/06/2026 | 19/06/2026 | PostgreSQL Series |
| 6 | **Advanced PostgreSQL on AWS - Part 2:** <br>&emsp; + Migration strategies (DMS) <br>&emsp; + High availability and disaster recovery <br>&emsp; + Extensions and stored procedures | 20/06/2026 | 20/06/2026 | PostgreSQL Series |

### Week 3 Achievements:

#### Data Analytics Foundations
* Understood the AWS analytics ecosystem and when to use each service
* Created Athena queries to analyze data stored in S3
* Optimized query performance with partitioning and bucketing
* Integrated Athena with QuickSight for ad‑hoc reporting

#### AWS Glue ETL
* Set up Glue Data Catalog by running crawlers
* Wrote ETL jobs in PySpark to transform data (filter, aggregate, join)
* Automated job execution with triggers and schedules
* Used job bookmarks to process incremental data

#### Amazon QuickSight
* Connected to Athena as a data source
* Created interactive dashboards with:
  - Bar charts, line graphs, heat maps
  - Filters and parameters for user‑driven analysis
  - Calculated fields and aggregations
* Published dashboards and shared with team

#### PostgreSQL on AWS
* Launched a production‑ready RDS PostgreSQL instance
* Configured Multi‑AZ for high availability
* Set up read replicas for read scaling
* Monitored performance with Performance Insights and CloudWatch
* Explored common extensions like `pg_stat_statements` and `postgis`

### Key Learning Outcomes:

> **Key Insight:** Data analytics is crucial for AI projects to understand data quality, perform exploratory analysis, and monitor model performance. Serverless tools like Athena and Glue enable cost‑effective, scalable analytics without infrastructure management.