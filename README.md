# 🛒 Enterprise Retail Analytics Platform on Microsoft Azure

An end-to-end **Azure Data Engineering** solution that demonstrates a modern **Metadata-Driven ETL Pipeline** using **Azure Data Factory, Azure Databricks, Azure Data Lake Storage Gen2, Delta Lake, Azure SQL Database, and Power BI**.

The project processes retail data from multiple heterogeneous sources, applies enterprise-grade transformations using the **Medallion Architecture (Bronze, Silver, Gold)**, and delivers business-ready analytics through interactive Power BI dashboards.

---

## 📌 Project Overview

Modern retail organizations receive data from multiple sources such as CSV files, relational databases, and REST APIs. Managing separate ETL pipelines for each source leads to increased maintenance, poor scalability, and inconsistent data quality.

This project addresses these challenges by implementing a **Metadata-Driven Azure Data Engineering Pipeline** capable of dynamically ingesting, validating, transforming, and analyzing retail data using reusable Azure services.

---

# 🏗 Solution Architecture

```
                    DATA SOURCES
        ┌────────────┬────────────┬────────────┐
        │            │            │
      CSV Files   Azure SQL     REST API
  (Products,Orders) (Customers) (Exchange Rates)
        │            │            │
        └────────────┴────────────┘
                     │
                     ▼
          Azure Data Factory (ADF)
        Metadata-Driven Orchestration
                     │
                     ▼
      Azure Data Lake Storage Gen2
               Landing Layer
                     │
                     ▼
           Azure Databricks (PySpark)
                     │
      ┌──────────────┼──────────────┐
      ▼              ▼              ▼
   Bronze         Silver        Gold Layer
 (Raw Delta)   (Validated)   (Fact & Dimensions)
                     │
                     ▼
           Azure SQL Database
                     │
                     ▼
                Power BI Reports
```

---

# 🚀 Features

- Metadata-Driven Azure Data Factory Pipeline
- Azure Data Lake Storage Gen2
- Medallion Architecture
- Delta Lake Implementation
- Azure Databricks (PySpark)
- Schema Evolution
- Reject Table Generation
- Data Validation
- Slowly Changing Dimension (SCD Type 2)
- Watermark-Based Incremental Loading
- Audit Logging
- Star Schema Data Warehouse
- Azure SQL Reporting Layer
- Interactive Power BI Dashboards

---

# ⚙ Technology Stack

| Category | Technology |
|----------|------------|
| Cloud Platform | Microsoft Azure |
| ETL Orchestration | Azure Data Factory |
| Data Processing | Azure Databricks |
| Programming | Python, PySpark |
| Data Lake | Azure Data Lake Storage Gen2 |
| Storage Format | Delta Lake |
| Database | Azure SQL Database |
| API | Exchange Rate REST API |
| Reporting | Power BI |
| Version Control | Git & GitHub |

---

# 📂 Project Structure

```
Enterprise-Retail-Analytics/
│
├── Azure_Data_Factory/
│   ├── Metadata Pipeline
│   ├── Linked Services
│   ├── Datasets
│   └── Pipelines
│
├── Databricks/
│   ├── 01_Data_Generation
│   ├── 02_Bronze
│   ├── 03_Silver
│   ├── 04_SCD_Process
│   ├── 05_Gold
│   └── 06_Data_Validation
│
├── SQL/
│   ├── Metadata Tables
│   ├── Watermark Tables
│   ├── Audit Logs
│   └── Gold Tables
│
├── Documentation/
│
├── PowerBI/
│
├── Images/
│
└── README.md
```

---

# 📊 Data Sources

The project ingests data from three different source types.

| Source | Type |
|---------|------|
| Products | CSV |
| Orders | CSV |
| Customers | Azure SQL Database |
| Exchange Rates | REST API |

---

# 🔄 Data Pipeline Workflow

1. Azure Data Factory reads metadata from Azure SQL Database.
2. Lookup Activity retrieves all active data sources.
3. ForEach Activity iterates through each metadata record.
4. Switch Activity determines the source type.
5. Copy Data Activity ingests data into the Landing layer.
6. Azure Databricks executes Bronze notebook.
7. Silver notebook performs cleansing and validation.
8. SCD Type 2 notebook maintains historical dimensions.
9. Gold notebook creates analytical tables.
10. Gold tables are loaded into Azure SQL Database.
11. Power BI generates interactive dashboards.

---

# 🥉 Bronze Layer

- Reads raw data from Landing
- Converts data into Delta Lake
- Preserves original records
- Adds ingestion timestamps
- Supports auditing and traceability

---

# 🥈 Silver Layer

- Data Type Conversion
- Duplicate Removal
- Null Value Handling
- Business Validation
- Reject Table Generation
- Schema Evolution
- Delta Table Creation

---

# 🥇 Gold Layer

Creates business-ready datasets including:

- Dim_Customer
- Dim_Product
- Fact_Sales

These tables follow a **Star Schema** optimized for Power BI reporting.

---

# 📈 Enterprise Features

✅ Metadata-Driven Pipeline

✅ Schema Evolution

✅ Reject Tables

✅ Delta Lake

✅ SCD Type 2

✅ Watermark-Based Incremental Loading

✅ Audit Logging

✅ Data Validation

✅ Star Schema

---

# 📊 Power BI Dashboard

The Power BI dashboard provides interactive insights including:

- Total Sales
- Total Orders
- Total Customers
- Average Order Value
- Monthly Sales Trend
- Sales by Category
- Customer Segmentation
- Product Performance
- Payment Method Analysis
- Store Performance

---

# 🧪 Data Validation

A dedicated Databricks validation notebook verifies:

- Bronze Layer
- Silver Layer
- Reject Tables
- Schema Validation
- SCD Type 2
- Gold Layer
- Fact Table Validation

Each validation produces a **PASS/FAIL** execution status.


# Steps to Perform This Architecture

This document outlines the complete implementation process for building the **Enterprise Retail Analytics Platform** using Microsoft Azure services. The architecture follows a metadata-driven ingestion framework and Medallion Architecture (Landing → Bronze → Silver → Gold) to create a scalable and automated data engineering solution.

---

# 1. Implement the High-Level Solution Architecture

## Overview

The solution integrates data from multiple heterogeneous sources and processes it through an automated Azure data engineering pipeline before making it available for business intelligence reporting.

### Technologies Used

- Azure Data Factory
- Azure Data Lake Storage Gen2
- Azure Databricks
- Azure SQL Database
- Power BI
- REST API
- CSV Files

---

## Step 1 – Configure Source Systems

Prepare all required data sources.

- CSV files
- Azure SQL Database
- REST API

Verify connectivity and ensure all datasets are available for ingestion.

---

## Step 2 – Create Azure Resources

Provision the following Azure resources:

- Azure Data Factory
- Azure Data Lake Storage Gen2
- Azure Databricks Workspace
- Azure SQL Database
- Power BI Workspace

---

## Step 3 – Configure Azure Data Factory

Create:

- Linked Services
- Datasets
- Integration Runtime (if required)

Configure secure connections to every source and destination.

---

## Step 4 – Implement Metadata-Driven Ingestion

Create metadata tables inside Azure SQL Database.

Store information such as:

- Source Name
- Source Type
- File Path
- Load Type
- Watermark Column
- Destination Table
- Active Status

Azure Data Factory will dynamically read these records during execution.

---

## Step 5 – Load Data into Landing Layer

Using Azure Data Factory Copy Activities:

- Read data from each source
- Store raw files inside the Landing container of ADLS Gen2

No transformation should occur in this stage.

---

## Step 6 – Execute Databricks Transformation Pipeline

Run notebooks sequentially:

1. Bronze Notebook
2. Silver Notebook
3. SCD Type 2 Notebook
4. Gold Notebook

---

## Step 7 – Load Curated Data

Load Gold Layer analytical tables into Azure SQL Database.

---

## Step 8 – Build Power BI Dashboards

Connect Power BI to Azure SQL Database.

Create:

- Sales Dashboard
- Customer Dashboard
- Product Dashboard
- KPI Reports

---

# 2. Implement the Low-Level Design Architecture

## Overview

The low-level design explains the detailed implementation of each layer within the Medallion Architecture.

---

## Step 1 – Generate Retail Dataset

Use Python scripts to generate sample retail data.

Example datasets:

- Customers
- Products
- Orders
- Sales
- Suppliers

---

## Step 2 – Configure Metadata Tables

Create metadata tables inside Azure SQL Database.

Examples:

- ingestion_metadata
- watermark_table
- audit_log

---

## Step 3 – Build Parameterized Azure Data Factory Pipelines

Create reusable pipelines using parameters.

Parameters may include:

- Source Name
- File Name
- Table Name
- Load Type

---

## Step 4 – Ingest Data into Landing Layer

Copy source data directly into:

```
ADLS Gen2
    └── Landing
```

This layer stores the original source files.

---

## Step 5 – Create Bronze Layer

Run the Bronze Notebook.

Tasks performed:

- Read Landing files
- Convert data into Delta Tables
- Add ingestion timestamp
- Preserve original records

Output:

```
Landing
    ↓
Bronze Delta Tables
```

---

## Step 6 – Create Silver Layer

Run the Silver Notebook.

Operations include:

- Datatype conversion
- Duplicate removal
- Null handling
- Data standardization
- Business validation
- Invalid record separation
- Data quality checks

Output:

```
Bronze
    ↓
Silver
```

---

## Step 7 – Generate Reject Tables

Create separate reject tables for records failing validation.

Common rejection reasons include:

- Missing values
- Invalid data types
- Business rule violations
- Duplicate records

---

## Step 8 – Enable Schema Evolution

Use Delta Lake schema evolution to automatically detect and merge new columns arriving from source systems.

---

## Step 9 – Implement Slowly Changing Dimension (SCD Type 2)

Apply SCD Type 2 for:

- Customer Dimension
- Product Dimension

Maintain historical versions using:

- EffectiveDate
- ExpiryDate
- IsCurrent
- Version

---

## Step 10 – Create Gold Layer

Generate analytical tables.

Examples:

- Dim_Product
- Dim_Customer
- Fact_Sales

These tables are optimized for reporting and analytics.

---

## Step 11 – Load Gold Tables into Azure SQL Database

Move analytical tables from ADLS Gen2 into Azure SQL Database.

This serves as the reporting layer.

---

## Step 12 – Create Power BI Reports

Connect Power BI with Azure SQL Database.

Develop interactive dashboards for:

- Sales Analysis
- Revenue Trends
- Customer Insights
- Product Performance

---

# 3. Implement the Azure Data Factory Metadata-Driven Pipeline

## Overview

The pipeline dynamically ingests multiple source systems using metadata-driven orchestration.

---

## Step 1 – Lookup Activity

Read metadata records from:

```
ingestion_metadata
```

Retrieve all active datasets for processing.

---

## Step 2 – ForEach Activity

Loop through every metadata record.

Each iteration processes one dataset independently.

---

## Step 3 – Switch Activity

Identify the source type.

Supported sources include:

- CSV
- Azure SQL Database
- REST API

Route execution accordingly.

---

## Step 4 – Copy Data Activity

Copy source data into the Landing container of Azure Data Lake Storage Gen2.

---

## Step 5 – Execute Bronze Notebook

Tasks performed:

- Read Landing files
- Convert to Delta format
- Add ingestion timestamp
- Store in Bronze layer

---

## Step 6 – Execute Silver Notebook

Perform:

- Datatype conversion
- Duplicate removal
- Null handling
- Business validation
- Reject table generation
- Schema evolution

---

## Step 7 – Execute SCD Type 2 Notebook

Maintain historical records for:

- Customer Dimension
- Product Dimension

Generate:

- EffectiveDate
- ExpiryDate
- IsCurrent
- Version

---

## Step 8 – Execute Gold Notebook

Create reporting-ready tables.

Examples:

- Dim_Product
- Dim_Customer
- Fact_Sales

Optimize data for analytical queries.

---

## Step 9 – Audit Logging

Record execution details including:

- Pipeline Name
- Start Time
- End Time
- Execution Status
- Rows Processed
- Error Message (if any)

---

## Step 10 – Watermark Update

Update the watermark table only after successful completion of the Gold layer.

This enables reliable incremental loading during future executions.

---

# Overall Workflow

```text
CSV / Azure SQL Database / REST API
                 │
                 ▼
      Azure Data Factory
                 │
                 ▼
      ADLS Gen2 - Landing
                 │
                 ▼
        Bronze Notebook
                 │
                 ▼
        Silver Notebook
                 │
                 ▼
      SCD Type 2 Notebook
                 │
                 ▼
         Gold Notebook
                 │
                 ▼
      Azure SQL Database
                 │
                 ▼
        Power BI Dashboard
```

---

# Implementation Summary

The architecture follows a fully automated metadata-driven approach where Azure Data Factory orchestrates data ingestion, Azure Data Lake Storage Gen2 stores data across Landing, Bronze, Silver, and Gold layers, Azure Databricks performs scalable data transformation using PySpark notebooks, Azure SQL Database serves as the reporting repository, and Power BI delivers interactive business intelligence dashboards. Audit logging and watermark mechanisms ensure reliable execution, historical tracking, and efficient incremental data loading.

