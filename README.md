# Microsoft-Fabric-Nyc-Taxi-End-To-End-Analytics-Project-
This project demonstrates an end-to-end data analytics and BI solution built using Microsoft Fabric, following modern data engineering, analytics, and governance best practices.

In this project, I ingested raw NYC Taxi data from a Lakehouse, processed it through staging and presentation layers using pipelines, Dataflow Gen2, and stored procedures, and delivered business insights through a Power BI semantic model and report.

## Key Components:
- Data ingestion with Fabric Pipelines
- Transformations using Dataflow Gen2
- Semantic model for analytics
- Interactive dashboards with Power BI

## Data Ingestion – Staging Layer
## 🔄 Data Ingestion – Staging Layer

![Staging Pipeline](images/pipeline_staging.png)


## Key features:

Script activity to determine latest processed date

Pipeline variables to manage incremental loads

Copy activity to load new data into staging tables

Stored procedures to:

Remove outlier dates

Load and maintain staging metadata
