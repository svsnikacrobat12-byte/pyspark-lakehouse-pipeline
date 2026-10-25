# ⚡ E-Commerce Lakehouse Pipeline w/ PySpark, Delta Lake & Databricks

![Project Banner](https://img.shields.io/badge/Databricks-Lakehouse-red?style=for-the-badge&logo=databricks)
![PySpark](https://img.shields.io/badge/Apache_Spark-PySpark-orange?style=for-the-badge&logo=apachespark)
![Delta Lake](https://img.shields.io/badge/Delta_Lake-ACID-blue?style=for-the-badge&logo=delta)

A production-grade cloud data engineering project analyzing and transforming high-velocity e-commerce data using a modern Lakehouse architecture. It replaces legacy Python ETL scripts with a scalable Databricks environment utilizing PySpark, Delta Lake, Unity Catalog, and Databricks SQL/Dashboards.

---

## 🧾 Executive Summary

- ✅ **Project Scope:** Built an end-to-end Medallion Lakehouse pipeline processing 183,000+ e-commerce transaction records across Bronze, Silver, and Gold layers.
- ✅ **Data Engineering & Modeling:** Applied PySpark transformations, regex parsing, window deduplication, multi-table joins, and denormalized Gold reporting views.
- ✅ **Distributed Performance:** Optimized Spark execution via Catalyst optimizers, the Photon engine, partition tuning (`repartition`/`coalesce`), and handling narrow vs. wide transformations.
- ✅ **Governance & Reliability:** Implemented ACID compliance, time travel via transaction logs (`_delta_log`), and centralized data governance using Unity Catalog.

If you only have a minute, review these core pipeline elements:

1. `1_Medallion_processing_dim` – Dimensional processing notebooks across Bronze, Silver, and Gold layers.
2. `3_Medallion_processing_fact` – Fact table processing pipelines for order items.
3. `Catalog_setup` – Unity Catalog and database/schema initialization script.

---

## 🧩 Problem & Context

E-commerce organizations frequently encounter severe operational hurdles as data scales:

- 🎯 **Scalability Crises:** Legacy single-node Python ETL pipelines struggle with surging data volumes and velocities, resulting in severe performance bottlenecks and frozen morning dashboards.
- 💰 **High Maintenance Overhead:** Fragile, fragmented architectures spanning multiple cloud tools (OLTP ➔ Python scripts ➔ S3 ➔ AWS Glue/Lambda ➔ Redshift) create billing obscurity and maintenance burdens.
- ⚖️ **Delayed Reporting:** Executive and marketing teams face severe delays accessing clean daily data.

---

## 🏗️ Architecture & Data Flow

### 1. Medallion Lakehouse Flow
The architecture progressively cleans, structures, and aggregates data from raw operational files into business-ready insights.


### 2. Distributed Spark Execution Flow
Under the hood, processing is distributed across worker nodes using cluster management and partitioned execution.


---

## 🧰 Tech Stack

- 🐤 **Compute Engine:** Apache Spark / PySpark for distributed data processing, DataFrame APIs, and Spark SQL.
- 🛡️ **Storage & Lakehouse Layer:** Delta Lake providing ACID transactions, the `_delta_log` transaction ledger, schema evolution, and time travel.
- 🔒 **Governance:** Databricks Unity Catalog enforcing a 3-level namespace (`catalog.schema.table`), automated data lineage, and fine-grained access control.
- 📊 **Analytics & BI:** Databricks SQL, Databricks Dashboards, and AI-Powered Genie natural language spaces.
- 🛠️ **Orchestration:** Databricks Jobs and Workflows for scheduled DAG task execution.

---

## 📂 Repository Structure

Based on the repository structure:

```text
pyspark-lakehouse-pipeline/
└── DataLakeHouse_Project/
    ├── 1_Medallion_processing_dim/     # Dimensional data ingestion & transformations
    ├── 3_Medallion_processing_fact/    # Fact table order items pipelines
    ├── Catalog_setup                   # Unity Catalog & schema initialization
    └── meta_data                       # Metadata documentation & audit files
