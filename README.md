🚖 Uber Real-Time Data Engineering Pipeline (Azure + Databricks)
📌 Project Overview

This project demonstrates an end-to-end real-time data engineering pipeline built using Microsoft Azure services and Apache Spark.

The pipeline simulates an Uber-like ride booking platform, where ride events are generated, streamed, processed, and transformed into an analytical data model using Medallion Architecture (Bronze → Silver → Gold).

The goal of this project is to showcase modern data engineering concepts such as:

Real-time data streaming

Batch + streaming hybrid pipelines

Lakehouse architecture

Slowly Changing Dimensions (SCD Type 2)

Star schema data modeling

Scalable cloud-based data processing

This project is designed to demonstrate practical data engineering skills using Azure and Databricks.

🏗️ Architecture

The pipeline follows a modern lakehouse architecture.

Event Producer
     │
     ▼
Azure Event Hub
     │
     ▼
Azure Data Lake Storage (Bronze Layer)
     │
     ▼
Azure Databricks (Spark Structured Streaming)
     │
     ▼
Silver Layer (Cleaned & Enriched Data)
     │
     ▼
Gold Layer (Star Schema Tables)
⚙️ Tech Stack
Programming

Python

PySpark

SQL

Azure Services

Azure Event Hub

Azure Data Factory

Azure Data Lake Storage Gen2

Azure Databricks

Data Engineering Concepts

Streaming Data Pipelines

Structured Streaming

Medallion Architecture

Slowly Changing Dimensions (Type 2)

Star Schema Data Modeling

Lakehouse Architecture

🔄 Data Pipeline Workflow

1️⃣ Event Generation

Ride booking events are generated from a simulated application and sent to Azure Event Hub.

2️⃣ Streaming Ingestion

Azure Event Hub acts as the streaming ingestion layer, capturing ride booking events in real time.

3️⃣ Batch Data Ingestion

Azure Data Factory loads static reference datasets such as:

Driver information

User information

Location data

These datasets are ingested into the Bronze layer of the data lake.

4️⃣ Bronze Layer

The Bronze layer stores raw data from both streaming and batch sources.

Data stored includes:

Raw ride events

Static reference tables

Source system datasets

5️⃣ Silver Layer

In the Silver layer, data is cleaned and transformed using Azure Databricks (PySpark).

Transformations include:

JSON parsing

Data cleansing

Joining reference tables

Creating unified datasets

6️⃣ Gold Layer

The Gold layer contains analytics-ready tables modeled using a Star Schema.

Fact Table
fact_rides
Dimension Tables
dim_driver
dim_user
dim_location
dim_date

These tables enable efficient analytical queries and BI reporting.

📂 Project Structure
Uber_DE_Project_Azure
│
├── Screenshots
│   ├── 1. Resource_group.png
│   ├── 2. Eventhub_Event Streaming.png
│   ├── 3. ADF_Pipeline to get static data from git.png
│   ├── 4. databricks pipeline.png
│   ├── 5. SCD_type2.png
│   └── 6. Medallian_Arch_Flow_databricks.PNG
│
└── README.md
📷 Project Screenshots
Azure Resource Group

Event Hub Streaming Setup

Azure Data Factory Pipeline (Static Data Ingestion)

Databricks Processing Pipeline

Slowly Changing Dimension (SCD Type 2)

Medallion Architecture Flow

⭐ Key Data Engineering Concepts Demonstrated

This project demonstrates the following core Data Engineering practices:

Real-time event streaming

Streaming data processing with Spark

Batch + streaming hybrid pipelines

Lakehouse architecture implementation

Medallion data architecture (Bronze / Silver / Gold)

Slowly Changing Dimensions (Type 2)

Star Schema data modeling

Cloud-based scalable data pipelines

🚀 Future Improvements

Possible enhancements to this project:

Add Power BI dashboards using Gold tables

Implement data quality checks

Add CI/CD pipeline using Azure DevOps

Add monitoring and alerting

Implement data lineage tracking

👩‍💻 Author

Lavanya K

Aspiring Data Engineer | Data Analyst
