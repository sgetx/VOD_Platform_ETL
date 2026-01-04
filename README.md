# VOD_Platform_ETL

# 1. Data Ingestion (Azure Data Factory)
I built a metadata-driven pipeline instead of static individual loads to ensure scalability.

I used a For-Each Loop to dynamically pull multiple files from GitHub APIs in one go.

I used Parameterized Linked Services so the same pipeline could handle different data sources.

I added a Validation Activity to check for source files before starting, which saved cloud costs.

I landed all raw data in ADLS Gen2 (Bronze Layer) to maintain a clear audit trail.

# 2. Data Processing (Databricks ETL)
I moved from batch processing to a modern incremental loading approach.

I used Databricks Autoloader to automatically detect and process new files in the Raw zone.

I enabled Schema Evolution and Checkpointing to handle data changes and ensure job recovery.

I cleaned complex data in the Silver Layer using PySpark and Window Functions.

I used If/Else logic in Databricks Workflows to manage different schedules for daily and weekly loads.

# 3. Quality & Governance (DLT & Unity Catalog)
I used Delta Live Tables (DLT) to manage transformations and table definitions together.

I applied DLT Expectations (Warn, Drop, Fail) to automatically enforce strict data quality rules.

I registered all assets in Unity Catalog to centralize security and permissions.

I used Unity Catalog to track data lineage, showing exactly how data moved from source to destination.

# 4. Serving & Analytics
I optimized final Gold tables using Z-Order clustering for faster query performance.

I connected Power BI directly to the Lakehouse via Databricks SQL Warehouses.

This setup allowed for real-time reporting without moving data out of the cloud environment.
