---
title: "Create DynamoDB Tables"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 5.3.2. </b> "
---

Create two tables in **On-demand** capacity mode (cost-optimized).

| Table | Partition key | Purpose |
|-------|---------------|---------|
| `student_records` | `student_id` (String) | Student academic data |
| `prediction_results` | `student_id` (String) | ML prediction output |

Steps for each table:

1. **DynamoDB → Create table**.
2. Enter table name and partition key `student_id` (String).
3. Capacity mode: **On-demand**.
4. Create.

![DynamoDB tables]( /images/5-Workshop/5.3-Backend-Pipeline/dynamodb-tables.png)