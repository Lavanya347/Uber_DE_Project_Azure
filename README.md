# 🚖 Uber Real-Time Data Engineering Pipeline on Azure

An **end-to-end streaming data engineering pipeline** built on **Microsoft Azure** that processes **real-time ride events and batch datasets** to create an **analytics-ready Star Schema model**.

The project simulates an **Uber-like ride booking platform** where ride events are streamed through Azure services, processed using **Databricks Structured Streaming**, and transformed into a **Lakehouse architecture (Bronze → Silver → Gold)** for analytics.

---

# 📌 Project Highlights

* Real-time event ingestion using **Azure Event Hub**
* Batch + Streaming hybrid data pipeline
* **Medallion Architecture** (Bronze / Silver / Gold)
* Data processing using **PySpark on Azure Databricks**
* **Metadata-driven pipelines**
* **Slowly Changing Dimensions (SCD Type 2)**
* **Star Schema dimensional modeling**

---

# 🏗️ Architecture Overview

The pipeline follows a **Lakehouse Architecture** built using Azure services.

## Pipeline Flow

```
Event Producer
      │
      ▼
Azure Event Hub
      │
      ▼
Azure Data Lake Storage (Bronze Layer)
      │
      ▼
Azure Databricks (Streaming + Batch Processing)
      │
      ▼
Silver Layer (Cleaned & Enriched Data)
      │
      ▼
Gold Layer (Star Schema for Analytics)
```

### System Architecture

![Architecture Diagram](Architecture/Architecture.png)

---

# ⚙️ Tech Stack

### Programming

* Python
* PySpark
* SQL

### Azure Services

* Azure Event Hub
* Azure Data Factory
* Azure Data Lake Storage Gen2
* Azure Databricks

### Data Engineering Concepts

* Real-Time Data Streaming
* Batch + Streaming Pipelines
* Medallion Architecture
* Metadata-Driven Pipelines
* Slowly Changing Dimensions (SCD Type 2)
* Star Schema Data Modeling
* Lakehouse Architecture

---

# ☁️ Azure Resource Setup

All Azure services used in the pipeline are deployed inside a dedicated **Azure Resource Group**.

The resource group contains:

* Azure Event Hub
* Azure Data Factory
* Azure Databricks
* Azure Data Lake Storage

### Azure Resource Group

![Azure Resources](Screenshots/1.%20Resource_group.png)

---

# 📡 Real-Time Streaming Pipeline (Azure Event Hub)

Ride booking events are simulated using **Python producer scripts** located in:

```
Event_Producer_Scripts/
```

The script generates ride events and sends them to **Azure Event Hub**, which acts as the **real-time ingestion layer**.

Event Hub enables scalable ingestion of streaming ride events before downstream processing.

### Event Hub Streaming

![EventHub Streaming](Screenshots/2.%20Eventhub_Event%20Streaming.png)

---

# 🔄 Batch Data Ingestion (Azure Data Factory)

Static datasets required for the pipeline are ingested using **Azure Data Factory**.

These datasets include:

* Driver information
* User information
* Location mapping data

The ADF pipeline fetches these datasets from GitHub and loads them into the **Bronze layer of Azure Data Lake**.

### Azure Data Factory Pipeline

![ADF Pipeline](Screenshots/3.%20ADF_Pipeline%20to%20get%20static%20data%20from%20git.png)

Pipeline configurations are available in:

```
ADF_Pipeline/
```

---

# ⚡ Data Processing using Azure Databricks

All transformations are implemented using **Azure Databricks with PySpark**.

Processing includes:

* Streaming ingestion from Event Hub
* JSON event parsing
* Data cleansing
* Joining streaming data with batch datasets
* Preparing datasets for analytical modeling

### Databricks Processing Pipeline

![Databricks Pipeline](Screenshots/4.%20databricks%20pipeline.png)

Transformation notebooks are stored in:

```
Code_Files/
```

---

# 🔁 Slowly Changing Dimensions (SCD Type 2)

The pipeline implements **Slowly Changing Dimension Type 2** to track historical changes in dimension tables such as **driver details**.

Key columns maintained:

```
effective_start_date
effective_end_date
is_current_record
```

This ensures historical tracking while maintaining the current active record.

### SCD Type 2 Implementation

![SCD Type 2](Screenshots/5.%20SCD_type2.png)

---

# 🪙 Medallion Architecture Implementation

The project follows the **Medallion Architecture pattern** to organize data into layers.

### Bronze Layer

Raw data ingested from:

* Event Hub streaming events
* Batch datasets via Azure Data Factory

### Silver Layer

Cleaned and enriched datasets created using PySpark transformations.

### Gold Layer

Analytics-ready data modeled using **Star Schema**, optimized for BI and reporting.

### Medallion Architecture Flow

![Medallion Architecture](Screenshots/6.%20Medallian_Arch_Flow_databricks.PNG)

---

# ⭐ Key Data Engineering Concepts Demonstrated

This project demonstrates several **production-grade data engineering practices**:

* Real-time streaming ingestion
* Hybrid batch + streaming pipelines
* Lakehouse architecture on Azure
* Metadata-driven ETL pipelines
* Medallion architecture (Bronze / Silver / Gold)
* Slowly Changing Dimensions (Type 2)
* Star schema dimensional modeling
* Scalable cloud-based data processing

---

# 📂 Repository Structure

```
Uber_DE_Project_Azure
│
├── ADF_Pipeline
│
├── Architecture
│   └── Architecture.png
│
├── Code_Files
│   ├── Bronze_Layer
│   ├── Silver_Layer
│   ├── Gold_Layer
│   └── Utilities
│
├── Data
│   ├── driver_data
│   ├── user_data
│   ├── ride_data
│   └── location_mapping
│
├── Event_Producer_Scripts
│
├── meta_data_configs
│
├── lk-adf-uberproject-dev
│
├── Screenshots
│
└── README.md
```

---

# 🚀 Future Improvements

Potential improvements for the project:

* Build **Power BI dashboards** on Gold layer tables
* Add **data quality validation checks**
* Implement **CI/CD pipelines using Azure DevOps**
* Add **monitoring and alerting for pipelines**
* Implement **data lineage tracking**

---

# 👩‍💻 Author

**Lavanya K**
Data Analyst | Aspiring Data Engineer

---

⭐ If you found this project useful, consider giving the repository a **star**.
