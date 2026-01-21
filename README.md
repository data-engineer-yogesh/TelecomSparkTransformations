# TelecomSparkTransformations

**Project Overview**
---
TelecomSparkTransformations is a hands-on Apache Spark project designed to practice DataFrame API, Spark SQL, joins, aggregations, window functions, and Delta Lake pipelines using a Telecom Analytics domain.
This project follows a Bronze → Silver → Gold architecture and is aligned with Databricks Certified Data Engineer exam patterns.

### 🎯 Learning Objectives

By completing this project, you will:
- Understand Spark DataFrame & SQL transformations
- Apply joins, filters, aggregations
- Implement window functions (ranking & rolling metrics)
- Build Delta Lake pipelines
- Learn DF vs SQL decision rules for exams and real projects


### Architecture Pattern
--- 

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

⚠️ Note: Bronze, Silver, and Gold are logical schemas and Delta tables,
not physical folders.


### 🏗️ Project Structure
---

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
---- 
#### Bronze Layer – Raw Ingestion

Notebook: 01_bronze_ingestion.ipynb

**Purpose**

- Ingest raw JSON data
- Store data as Bronze Delta tables
- Minimal or no transformation
- Bronze Tables Created

```
bronze.subscribers
bronze.call_records
bronze.data_usage
bronze.recharge

```

**Key Characteristics**

- Append-only
- Schema-on-read
- Source-of-truth data

---
#### Silver Layer – Transformations

Notebook: 02_silver_transformations.ipynb

**Purpose**

- Clean and enrich telecom data
- Apply business logic
- Join multiple Bronze tables
- Silver Tables Created

```
silver.usage_enriched

```
**Transformations Applied**

- Joins between subscribers, calls, and data usage
- Filtering invalid or zero-usage records
- Derived usage metrics
---

#### Gold Layer – Analytics

Notebook: 03_gold_analytics.ipynb

**Purpose**
- Create analytics-ready tables
- Support reporting and insights
- Gold Tables Created
  
```
gold.subscriber_metrics
gold.daily_network_usage

```

**Metrics Covered**

- Total usage per subscriber
- Average daily usage
- Active usage days
- Subscriber ranking by usage
---

#### 🪟 Window Functions

This project covers exam-critical window functions, including:

- RANK() – Subscriber ranking based on usage
- Rolling 7-day usage using partitioned windows
- Time-based aggregations
---
**DataFrame vs Spark SQL – Decision Rules**
```
| Scenario                         | Preferred Approach |
| -------------------------------- | ------------------ |
| Complex transformation logic     | DataFrame API      |
| Reusable pipeline logic          | DataFrame API      |
| Aggregations & reporting         | Spark SQL          |
| Window functions (exam-friendly) | Spark SQL          |
| Ad-hoc analysis                  | Spark SQL          |

```
---

#### Technologies Used
- Apache Spark (PySpark)
- Spark SQL
- Delta Lake
- Databricks Notebooks
- JSON data sources
- Unity Catalog (design-level)
-----

#### Future Enhancements
- Incremental loads using MERGE INTO
- OPTIMIZE & Z-ORDER implementation
- Data quality checks
- Streaming ingestion for CDR data

---

## ⭐ If You Found This Useful

Give this repo a ⭐ and feel free to fork or extend it!

Happy Learning 🚀
