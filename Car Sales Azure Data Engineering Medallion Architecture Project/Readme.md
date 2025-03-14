# Azure End-to-End Data Engineering Project: Car Sales - Medallion Framework

## Project Summary
This initiative focuses on building a scalable data engineering solution on Microsoft Azure to process car sales data efficiently. The Medallion Framework structures data flow into three layers—Bronze, Silver, and Gold—ensuring smooth data transformation from raw ingestion to analytics-ready insights. Automated workflows enhance scalability and efficiency.

## Architecture Breakdown
The Medallion Framework consists of the following structured stages:

- **Bronze Layer** – Stores raw, unprocessed data.
- **Silver Layer** – Contains refined and enriched data.
- **Gold Layer** – Provides structured, analytics-ready data.

![Architecture View](https://github.com/Chirudc/End_to_End_Azure_Data_Engineering_Medallion_Architecture_Project/blob/main/Car%20Sales%20Azure%20Data%20Engineering%20Medallion%20Architecture%20Project/Images/Medallion%20Architecture.png)

## Core Features
- **Three-Layered Data Flow**: Data transitions through distinct layers for efficient processing and management.
- **Automated Data Pipelines**: Azure Data Factory automates ingestion and transformation workflows.
- **Incremental Data Updates**: Ensures new data is appended to the Bronze tier for optimized processing.
- **Data Cleaning & Transformation**: Databricks refines raw data for analytical use.
- **Star Schema & SCD Type-1**: Implements structured data modeling with historical update mechanisms.

## Technology Stack
- **Azure Data Factory** – Manages data orchestration and movement.
- **Azure SQL Database** – Stores raw data before processing.
- **Azure Data Lake Gen 2** – Facilitates tiered storage across Bronze, Silver, and Gold layers.
- **Azure Databricks** – Conducts data transformation and enrichment.
- **Star Schema & SCD Type-1** – Enhances data modeling and historical tracking.

## End-to-End Process Overview
### Raw Data Ingestion
- Raw data is extracted from an external source using Azure Data Factory’s Copy Activity.
- The extracted data is stored in the source table within Azure SQL Database.
- A parameterized process is implemented to enable dynamic file selection for ingestion.

### Incremental Data Processing
- Water tables are utilized to track the last loaded date and facilitate incremental data processing.
- Azure Data Factory’s Lookup, Copy Activity, and Stored Procedure Activities automate the loading process.

### Secure Data Management with Unity Catalog
- Azure Databricks integrates with Unity Catalog to enforce role-based access and secure data handling.
- External tables are created to establish seamless linkage between the data lake and Databricks.

### Data Transformation & Structuring
- Databricks processes and refines the data, applying necessary transformations to convert it into structured formats.
- The **Silver layer** is created by cleaning, enriching, and standardizing the raw data.
- The **Gold layer** is formed by structuring the refined data into a **star schema**, making it optimized for analysis and reporting.

### Workflow Automation & Validation
- Databricks notebooks are embedded within an integrated workflow to automate transformation tasks.
- ADF Copy Activity verifies incremental datasets to ensure accuracy and completeness before final validation.

### Final Data Preparation for Analytics and Reporting
- The **Gold layer** serves as the ultimate refined dataset, containing cleaned and enriched data.
- This structured data is optimized for business intelligence, reporting, and advanced analytics applications.
- It ensures seamless integration with visualization tools and supports data-driven decision-making.

## Pipeline Design
### Pipeline 1: Ingestion Mechanism
- Pulls data from GitHub and loads it into Azure SQL Database.

![Pipeline1](https://github.com/Chirudc/End_to_End_Azure_Data_Engineering_Medallion_Architecture_Project/blob/main/Car%20Sales%20Azure%20Data%20Engineering%20Medallion%20Architecture%20Project/Images/Pipeline1.png)

### Pipeline 2: Incremental Data Processing
- Ensures only new data is added to the Bronze Layer.
- Azure Data Factory’s expression builder dynamically filters new records based on date criteria.
- A stored procedure extracts the latest available date to process only fresh data.

![Pipeline2](https://github.com/Chirudc/End_to_End_Azure_Data_Engineering_Medallion_Architecture_Project/blob/main/Car%20Sales%20Azure%20Data%20Engineering%20Medallion%20Architecture%20Project/Images/Pipeline2.png)


### SQL-Based Data Management
- SQL tables and stored procedures support data refinement and structured processing.

![SQL Query](https://github.com/Chirudc/End_to_End_Azure_Data_Engineering_Medallion_Architecture_Project/blob/main/Car%20Sales%20Azure%20Data%20Engineering%20Medallion%20Architecture%20Project/Images/SQL%20Query.png)

![Stored Procedure](https://github.com/Chirudc/End_to_End_Azure_Data_Engineering_Medallion_Architecture_Project/blob/main/Car%20Sales%20Azure%20Data%20Engineering%20Medallion%20Architecture%20Project/Images/Stored%20Procedure.png)

### Databricks Pipeline Run: Star Schema Transformation
- This image represnts Databricks Job Run for the Data-Model Pipeline, executing the Star Schema Transformation in the Azure End-to-End Data Engineering Project. It converts raw Silver Layer data into a structured Star Schema Model for optimized analytics.

![Data Model Pipeline](https://github.com/Chirudc/End_to_End_Azure_Data_Engineering_Medallion_Architecture_Project/blob/main/Car%20Sales%20Azure%20Data%20Engineering%20Medallion%20Architecture%20Project/Images/Data%20Modeling.png)

### Optimized Incremental Data Processing
- Integration of Databricks within Azure Data Factory enhances efficiency.
- After data is ingested into the Bronze Layer, Databricks processes it further into Silver and Gold Layers.
- This end-to-end integration automates data transformation workflows.
- The Databricks notebook performs data cleaning, transformation, and structuring for analytical readiness.

![Updated Incremental](https://github.com/Chirudc/End_to_End_Azure_Data_Engineering_Medallion_Architecture_Project/blob/main/Car%20Sales%20Azure%20Data%20Engineering%20Medallion%20Architecture%20Project/Images/Optimized_Incremental_Loading.png)

## Azure Resource Deployment
- Overview of deployed Azure resources for seamless execution of the project.

![Resource Group](https://github.com/Chirudc/End_to_End_Azure_Data_Engineering_Medallion_Architecture_Project/blob/main/Car%20Sales%20Azure%20Data%20Engineering%20Medallion%20Architecture%20Project/Images/Resource%20Group.png)

## Deployment & Execution Guide
### Prerequisites
- Active Azure Subscription with access to **Data Factory, Databricks, and Data Lake**.
- Familiarity with creating pipelines in Azure Data Factory.
- Configured Azure Databricks workspace and cluster.
- Access to a GitHub repository containing raw data.
- Azure SQL Database for initial data storage.

### Implementation Steps
1. **Set Up Azure Data Factory Pipelines**:  
   - **Pipeline 1**: Ingest data from GitHub into Azure SQL Database.  
   - **Pipeline 2**: Automate incremental data movement to the Bronze Layer of Azure Data Lake.
2. **Deploy Azure Databricks**:  
   - Establish a workspace and configure a cluster.  
   - Import and execute Databricks notebooks for data transformation.
3. **Validate Data Flow**:  
   - Confirm raw data is stored correctly in Azure SQL Database.  
   - Ensure seamless data movement through Bronze, Silver, and Gold Layers in Data Lake.
4. **Generate Star Schema**:  
   - Execute Databricks jobs to structure data into a **star schema**.  
   - Implement **SCD Type-1** for historical updates.
5. **Customize as Required**:  
   - Modify workflows, transformations, and notebooks as per project needs.  
   - Implement monitoring and error-handling mechanisms.

## Post-Execution Analysis
- The **Gold Layer** will hold fully processed, analytics-ready data upon pipeline completion.
- This structured dataset can be leveraged for **business intelligence, visualization, and predictive analytics**.
