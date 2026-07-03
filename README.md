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

