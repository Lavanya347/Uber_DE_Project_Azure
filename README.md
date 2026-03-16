🚖 Uber Real-Time Data Engineering Pipeline on Azure
📌 Project Overview

This project demonstrates an end-to-end Data Engineering pipeline on Microsoft Azure that processes both real-time streaming data and batch data to create an analytics-ready data model.

The system simulates an Uber-like ride booking platform where ride events are streamed in real time, ingested into Azure services, processed using Azure Databricks (PySpark), and modeled using a Medallion Architecture (Bronze → Silver → Gold).

This project showcases real-world data engineering practices used in production systems such as streaming ingestion, scalable ETL pipelines, metadata-driven pipelines, and dimensional modeling.

🏗️ Architecture Overview

The pipeline follows a Lakehouse Architecture built using Azure services.

Pipeline Flow

Event Producer
⬇
Azure Event Hub (Streaming Ingestion)
⬇
Azure Data Lake Storage – Bronze Layer
⬇
Azure Databricks (Streaming + Batch Processing)
⬇
Silver Layer (Cleaned & Enriched Data)
⬇
Gold Layer (Star Schema for Analytics)

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

Real-Time Data Streaming

Batch + Streaming Pipelines

Medallion Architecture

Metadata-Driven Pipelines

Slowly Changing Dimensions (SCD Type 2)

Star Schema Data Modeling

Lakehouse Architecture

📂 Repository Structure
Uber_DE_Project_Azure
│
├── ADF_Pipeline
│   └── Azure Data Factory pipeline JSON files
│
├── Architecture
│   └── Architecture diagrams for the pipeline
│
├── Code_Files
│   ├── Bronze_Layer
│   │   └── Raw data ingestion notebooks/scripts
│   │
│   ├── Silver_Layer
│   │   └── Data transformation notebooks
│   │
│   ├── Gold_Layer
│   │   └── Star schema creation scripts
│   │
│   └── Utilities
│       └── Helper scripts for transformations
│
├── Data
│   ├── driver_data
│   ├── user_data
│   ├── ride_data
│   └── location_mapping
│
├── Event_Producer_Scripts
│   └── Python scripts that simulate ride booking events
│
├── meta_data_configs
│   └── Metadata configuration files used in the pipeline
│
├── lk-adf-uberproject-dev
│   └── Azure Data Factory ARM templates
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
☁️ Azure Resource Setup

All Azure services required for the pipeline are created within a dedicated Azure Resource Group.

The resource group includes:

Azure Event Hub

Azure Data Factory

Azure Databricks

Azure Data Lake Storage

Azure Resource Group

📡 Real-Time Event Streaming (Azure Event Hub)

Ride booking events are simulated using Python producer scripts located in:

Event_Producer_Scripts/

These scripts generate ride events and send them to Azure Event Hub, which acts as the real-time ingestion layer.

Event Hub enables scalable ingestion of streaming data before it is processed by downstream systems.

Event Hub Streaming Setup

🔄 Batch Data Ingestion (Azure Data Factory)

Static datasets required for the pipeline are ingested using Azure Data Factory pipelines.

The ADF pipelines load reference datasets from GitHub into Azure Data Lake Storage (Bronze Layer).

Examples of batch datasets:

Driver information

User information

City/location mapping

Pipeline definitions are stored in:

ADF_Pipeline/
Azure Data Factory Pipeline

⚡ Data Processing (Azure Databricks)

All transformations and processing are implemented using Azure Databricks with PySpark.

The transformation scripts are organized in:

Code_Files/

Processing steps include:

Streaming ingestion from Event Hub

JSON event parsing

Data cleansing

Joining streaming data with reference tables

Preparing datasets for analytical modeling

Databricks Processing Pipeline

🔁 Slowly Changing Dimension (SCD Type 2)

The pipeline implements SCD Type 2 logic to track historical changes in dimension tables such as driver details.

Key columns maintained:

effective_start_date

effective_end_date

is_current_record

This allows maintaining a complete history of dimension changes.

SCD Type 2 Implementation

🪙 Medallion Architecture Implementation

The pipeline uses the Medallion Architecture, organizing data into three layers.

Bronze Layer

Raw ingested data from streaming and batch sources.

Silver Layer

Cleaned and transformed data with business logic applied.

Gold Layer

Analytics-ready tables modeled using Star Schema.

These tables can be used for BI tools such as Power BI.

Medallion Architecture Flow

⭐ Key Data Engineering Concepts Demonstrated

This project demonstrates multiple production-grade data engineering practices:

Real-time streaming ingestion

Batch + streaming hybrid data pipelines

Lakehouse architecture

Metadata-driven pipeline design

Medallion architecture (Bronze / Silver / Gold)

Slowly Changing Dimensions (Type 2)

Star schema data modeling

Scalable cloud-based data pipelines

🚀 Future Improvements

Possible enhancements for this project:

Build Power BI dashboards on Gold tables

Add data quality validation checks

Implement CI/CD pipelines with Azure DevOps

Add pipeline monitoring and alerting

Implement data lineage tracking

👩‍💻 Author

Lavanya K
Aspiring Data Engineer | Data Analyst
