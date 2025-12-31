# Microsoft-Fabric-Nyc-Taxi-End-To-End-Analytics-Project-
This project demonstrates an end-to-end data analytics and BI solution built using Microsoft Fabric, following modern data engineering, analytics, and governance best practices. This project demonstrates how raw data can be ingested, transformed, modeled, and visualized to support data-driven decision-making.

In this project, I ingested raw NYC Taxi data from a Lakehouse, processed it through staging and presentation layers using data pipelines, Dataflow Gen2, and stored procedures, and delivered business insights through a Power BI semantic model and report.

## Key Components:
- Workspace and Environment Setup
- Data Source Identification and Lakehouse Setup
- Designing the Staging Layer Strategy
- Building the Staging Pipeline (Ingestion Pipeline)
- Designing the Presentation Layer
- Data Transformation Using Dataflow Gen2
- Building Presentation Pipeline
- Semantic model for analytics
- Interactive dashboards with Power BI

## Workspace and Environment Setup

I created a Microsoft Fabric workspace, which serves as the logical container for all analytics assets. This workspace hosts the Lakehouse, Warehouse, pipelines, Dataflow Gen2, semantic model, and Power BI report.

Proper workspace organization is critical because:

It enforces governance and access control

It ensures all assets can be orchestrated together

It reflects enterprise data domain separation

In the workspace, naming conventions were established to clearly distinguish lakehouse, warehouse, data flow Gen 2 and pipeline activities.



## Data Source Identification and Lakehouse Setup

In this project, I used NYC Taxi Trip CSV files as the raw data source. These files were uploaded into a Lakehouse within OneLake, which acts as the landing zone.

I used the Lakehouse because:

It supports large-scale file storage

It integrates seamlessly with Fabric Pipelines and Dataflows

It preserves raw data for auditing and reprocessing

No transformations were applied at this stage. I left the raw data intentionally unchanged  to maintain data lineage and traceability.


## Designing the Staging Layer Strategy
Before i built the data pipelines, i created a staging layer. The staging layer served as an intermediate processing zone between raw data and processed analytics data.

I created a Fabric Warehouse in the workspaced and then created a staging schema in the warehouse where the raw data will be sotred after ingestion.


## Building the Staging Pipeline (Ingestion Pipeline)
i created a staging  pipeline which is responsible for ingesting rwa NYC taxi data from the Lakehouse into staging table in the Fabrc Warehouse.

The staging pipeline activities included;

I wrote and SQL script that retrieves the most recent processed date from a metadata table. This allows the pipeline to determine which records are new and need to be ingested.

I created a pipeline variable Activity to drive incremental loading logic based on month of each raw data record. This hlped prevet reprocessing of historical data

I created a pipleine copy activity to transfer on the new records from the Lakehouse into staging tables in the Warehouse.

Using SQL scripts, I created a stored procedure activity to remove invalid or outlier dates, uodate metadata tables and maintain ingestion audit infromation enabling  enterprise-grade ingestion patterns, 
including incremental loads, metadata-driven processing, and data quality safeguards.

## Designing the Presentation Layer
The presentation layer represents the processed, analytics-ready data used for reporting and decision-making.
The presentation tables:
Contains business-friendly column names.
Applies consistent business rules.
Support aggregations and analytics queries.

The presentation layer was also implemented in the Fabric Warehouse to take advantage of SQL performance and integration with Power BI semantic models.

## Data Transformation Using Dataflow Gen2
I Transformed the data from the staging to presentation using Dataflow Gen2.

The transformation steps included:

Cleaning and standardizing datetime fields

Validating numeric columns (fares, distances, passengers)

Removing null or invalid records

Creating business-ready fields

Preparing aggregated datasets


## Building Presentation Pipeline
I created a pipeline for the presentation processing.

This pipeline:

Triggers the Dataflow Gen2 execution

Runs stored procedures to load or merge presentation tables into the presentation schema

Ensures dependencies are executed in the correct order.

