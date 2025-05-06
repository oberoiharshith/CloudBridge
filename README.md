# CloudBridge: Azure Lakehouse for E-Commerce Analytics

## Project Overview

CloudBridge is an end-to-end modern data engineering project that builds a scalable **Azure Lakehouse** architecture for real-time e-commerce analytics. It demonstrates best practices in cloud data ingestion, transformation, and visualization, leveraging the **Medallion Architecture** (Bronze → Silver → Gold) to power auto-refreshing dashboards with **sub-5-minute latency**.

The project uses real-world datasets from **Olist** (Brazilian e-commerce platform) and additional documents from **MongoDB** to simulate a multi-source enterprise data environment.

---

## Architecture Diagram

**Azure Components Used:**

* **Azure Data Factory (ADF):** Orchestration and ETL pipelines
* **Azure Data Lake Storage (ADLS):** Centralized raw and curated data storage
* **Azure Databricks:** Data transformation, Medallion structure (Bronze/Silver/Gold)
* **Azure Synapse Analytics:** Query serving layer (DW)
* **Power BI:** Business intelligence and real-time dashboarding

---

## Data Flow

1. **Ingestion:**

   * Olist CSV datasets ingested via ADF pipelines into **ADLS Bronze Layer**.
   * MongoDB collections extracted and ingested using ADF MongoDB connector.

2. **Transformation:**

   * Databricks notebooks process Bronze data.
   * Cleaning, normalization, joining across Olist tables.
   * Creation of curated Silver tables (optimized Parquet format).
   * Aggregations and business metrics computation for Gold tables.

3. **Serving:**

   * Gold data exposed to Synapse external tables.
   * Power BI connects live to Synapse for dashboards with **<5 min auto-refresh latency**.

---

## Key Features

* **Medallion Architecture:** Ensures reliability, modular transformations, and scalability.
* **Real-Time Insights:** Dashboards refresh in near real-time from Synapse sources.
* **Multi-Source Integration:** Structured (CSV) + Semi-Structured (MongoDB) data combined.
* **Optimized Data Modeling:** Parquet, Delta Lake best practices applied.
* **Orchestration:** Event-driven and scheduled pipelines via ADF.

---

## Technologies Used

* Azure Data Factory (ADF)
* Azure Data Lake Storage (ADLS Gen2)
* Azure Databricks (PySpark, Delta Lake)
* Azure Synapse Analytics
* Power BI
* MongoDB Atlas
* Python (PySpark ETL scripts)
* SQL (Azure Synapse external tables, views)

---

## Setup Instructions

1. Deploy Storage Accounts and configure containers: **bronze**, **silver**, **gold**.
2. Create ADF pipelines for:

   * Olist CSV ingestion
   * MongoDB collection ingestion
3. Setup Databricks cluster and import notebooks for transformation:

   * Bronze → Silver processing
   * Silver → Gold processing
4. Configure Synapse external tables on Gold data.
5. Build Power BI reports by connecting to Synapse with DirectQuery.

---

## Business Use Cases Demonstrated

* Order volume tracking across regions.
* Customer churn prediction indicators.
* Delivery delays monitoring.
* Product review sentiment analysis.
* Revenue and profitability analytics.

---

## Future Enhancements

* Add event-driven triggers based on ADLS file arrivals.
* Integrate Azure Stream Analytics for real-time ingestion.
* Deploy ML models for delivery time prediction and recommendation engines.
* Use Azure Data Share for secure data collaboration.

---

## Author
**Harshith Oberoi**

