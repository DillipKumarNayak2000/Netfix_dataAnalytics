# 🎬 Netflix Data Engineering Project
This repository showcases a full-scale data engineering pipeline built to ingest, transform, validate, and analyze Netflix datasets using modern cloud-native tools. The project follows a multi-layered architecture (Bronze → Silver → Gold) and leverages Delta Lake and Databricks for scalable, reliable data processing.

## 📌 Project Overview
The pipeline is divided into four key phases:
🔹 Phase 1: Ingestion (Bronze Layer)
- Ingested raw Netflix dataset from GitHub API using Azure Data Factory
- Landed data in Azure Data Lake Storage (ADLS) in JSON/CSV format
- Established the Bronze layer for raw, unprocessed data
## 🔹 Phase 2: Transformation (Silver Layer)
- Created parameterized modular notebooks in Databricks to process Bronze → Silver
- Applied data cleaning:
- Standardized column names and datatypes
- Removed duplicates and nulls
- Handled malformed records
- Automated daily ingestion using AutoLoader and scheduled workflows
##🔹 Phase 3: Data Quality & Streaming with DLT
- Implemented Delta Live Tables (DLT) for:
- Data quality rules (constraints, expectations, validity checks)
- Schema enforcement
- Built streaming tables on top of Silver Delta tables to simulate real-time ingestion
- Performed aggregations (e.g., movie counts by genre, release year, ratings)
##🔹 Phase 4: Analytics (Gold Layer)
- Transformed curated Silver data into business-ready Gold tables using DLT workflows
- Aggregated and enriched data for downstream analytics and reporting.
flowchart TD

## 🏗️ Project Architecture
📦 netflix-data-pipeline
┣ 📂 notebooks
┃ ┣ 📜 ingest_bronze.py
┃ ┣ 📜 bronze_to_silver.py
┃ ┣ 📜 transformations_silver.py
┃ ┣ 📜 dlt_quality_pipeline.py
┃ ┗ 📜 silver_to_gold_dlt.py
┣ 📂 workflows
┃ ┣ 📜 bronze_to_silver_job.json
┃ ┗ 📜 dlt_gold_workflow.json
┣ 📜 README.md



## 🚀 Getting Started
- Clone the repository
- Configure Azure Data Factory to connect to the GitHub API
- Set up ADLS containers for Bronze, Silver, and Gold layers
- Import notebooks into Databricks and configure AutoLoader
- Deploy DLT pipelines and workflows for streaming and analytics

## 📈 Future Enhancements
- Integrate real-time user engagement metrics
- Add dashboarding layer using Power BI or Tableau
- Implement CI/CD for pipeline deployment

## 🏗️Flow Architecture

```plaintext
                 ┌──────────────────────────┐
                 │   GitHub API (Netflix)   │
                 └────────────┬─────────────┘
                              │
                    ┌─────────▼─────────┐
                    │ Azure Data Factory│
                    │   (Data Ingestion)│
                    └─────────┬─────────┘
                              │
                              ▼
                   ┌─────────────────────┐
                   │   ADLS (Bronze)     │
                   └─────────────────────┘
                              │
                              ▼
                  ┌──────────────────────┐
                  │ Databricks (Silver)  │
                  │   Cleaning + ETL     │
                  └──────────────────────┘
                              │
                              ▼
                 ┌──────────────────────────┐
                 │ Delta Live Tables (DLT)  │
                 │  Quality + Streaming     │
                 └──────────────────────────┘
                              │
                              ▼
                ┌───────────────────────────┐
                │ ADLS / Databricks (Gold)  │
                │  Analytics & Reporting    │
                └───────────────────────────┘




