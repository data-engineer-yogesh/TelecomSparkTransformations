# TelecomSparkTransformations

**Project Overview**
TelecomSparkTransformations is a hands-on Apache Spark project designed to practice Spark DataFrame API and Spark SQL using a Telecom Analytics domain.  
The project focuses on joins, aggregations, window functions, and Delta Lake pipelines, and follows the Bronze–Silver–Gold Lakehouse architecture.

This project is aligned with Databricks Certified Data Engineer exam patterns and real-world data engineering use cases.



## Learning Objectives
By completing this project, you will:
- Understand Spark DataFrame and Spark SQL transformations
- Apply joins, filters, and aggregations
- Implement window functions for ranking and rolling metrics
- Build Delta Lake pipelines using Bronze, Silver, and Gold layers
- Learn DataFrame versus Spark SQL decision rules for exams and production projects


## Architecture Pattern

```
This project uses the Lakehouse architecture:
Raw JSON Data
     ↓
Bronze Layer (Raw Delta Tables)
     ↓
Silver Layer (Cleaned & Enriched Tables)
     ↓
Gold Layer (Analytics & Business Metrics)

```


**Note:** *Bronze, Silver, and Gold are logical schemas implemented as Delta tables, not physical folders.*


## Project Structure

```

TelecomSparkTransformations/
│
├── data/
│   ├── subscribers.json        # Subscriber master data
│   ├── call_records.json       # Call Detail Records (CDR)
│   ├── data_usage.json         # Mobile internet usage events
│   ├── recharge.json           # Recharge & payment transactions
│
├── notebooks/
│   ├── 01_bronze_ingestion.ipynb        # Raw JSON → Bronze Delta tables
│   ├── 02_silver_transformations.ipynb  # Joins, filters, enrichments
│   ├── 03_gold_analytics.ipynb          # Aggregations & window functions
│   ├── 04_exam_decision_rules.ipynb     # DF vs SQL + exam patterns
│
├── diagrams/
│   └── telecom_lakehouse_architecture.png   # Bronze–Silver–Gold flow
│
├── Unity_Catalog_Design.ipynb
├── Tables_Design.ipynb
│
└── README.md

```

---

## Bronze Layer – Raw Ingestion

**Notebook**

*01_bronze_ingestion.ipynb*

### Purpose
- Ingest raw JSON telecom data
- Store data as Bronze Delta tables
- Apply minimal or no transformations

### Bronze Tables
- bronze.subscribers
- bronze.call_records
- bronze.data_usage
- bronze.recharge

### Key Characteristics
- Append-only ingestion
- Schema-on-read
- Source-of-truth data


## Silver Layer – Transformations

**Notebook**

*02_silver_transformations.ipynb*

### Purpose
- Clean and enrich telecom datasets
- Apply business logic
- Join multiple Bronze tables

### Silver Tables
- silver.usage_enriched

### Transformations Applied
- Joins between subscribers, call records, and data usage
- Filtering invalid or zero-usage records
- Derived usage and activity metrics

## Gold Layer – Analytics

**Notebook**

*03_gold_analytics.ipynb*

### Purpose
- Create analytics-ready datasets
- Support reporting and business insights

### Gold Tables
- gold.subscriber_metrics
- gold.daily_network_usage

### Metrics Covered
- Total usage per subscriber
- Average daily usage
- Active usage days
- Subscriber ranking by usage


## Window Functions
This project covers window functions commonly tested in certification exams and used in analytics workloads:
- RANK for subscriber ranking based on usage
- Rolling seven-day usage metrics using partitioned windows
- Time-based aggregations

---

## DataFrame vs Spark SQL – Decision Rules

| Scenario                          | Preferred Approach |
|----------------------------------|-------------------|
| Complex transformation logic     | DataFrame API     |
| Reusable pipeline logic          | DataFrame API     |
| Aggregations and reporting       | Spark SQL         |
| Window functions (exam-friendly) | Spark SQL         |
| Ad-hoc analysis                  | Spark SQL         |

---

## Technologies Used
- Apache Spark (PySpark)
- Spark SQL
- Delta Lake
- Databricks Notebooks
- JSON data sources
- Unity Catalog (design-level)

---

## Future Enhancements
- Incremental loads using MERGE INTO
- OPTIMIZE and Z-ORDER implementation
- Data quality checks
- Streaming ingestion for CDR data

---

## License
This project is intended for learning and demonstration purposes.
