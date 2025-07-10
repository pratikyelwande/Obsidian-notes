### Types of Data
- **Structured Data:**
    
    - **Definition:** Highly organized, fits into fixed rows/columns.
        
    - **Example:** SQL databases, Excel spreadsheets (customer IDs, names, dates).
        
    - **Key:** Easy to query with SQL.
        
- **Semi-structured Data:**
    
    - **Definition:** Has some organization (tags, markers) but no rigid schema.
        
    - **Example:** JSON files, XML files, log files.
        
    - **Key:** More flexible than structured, easier to manage than unstructured.
        
- **Unstructured Data:**
    
    - **Definition:** No predefined format or organization.
        
    - **Example:** Text documents, images, videos, audio files.
        
    - **Key:** Requires advanced tools (e.g., NLP, computer vision, big data frameworks) for analysis.



![[{A8B46DB9-8328-408A-ABDE-D771D938DC84}.png]]

|Feature|**Data Lake**|**Delta Lake**|**Data Warehouse**|
|---|---|---|---|
|**Definition**|A centralized repository storing _raw_, diverse data in its native format.|An **open-source storage layer** built on a Data Lake, adding reliability and performance.|A highly structured repository for _processed_, historical data for analytics.|
|**Primary Purpose**|Ingest and store all data at scale for future use, exploration, AI/ML.|Bring data reliability (ACID), schema enforcement, and performance to Data Lakes.|Optimized for traditional BI, reporting, and structured analytical queries.|
|**Data Types**|Structured, Semi-structured, Unstructured (all)|Structured, Semi-structured (adds structure to lake data)|Primarily Structured|
|**Schema**|**Schema-on-Read:** Schema applied at query time. Highly flexible.|**Flexible Schema Enforcement/Evolution:** Can enforce schema on write for quality, but also allows evolution.|**Schema-on-Write:** Schema defined strictly before data is loaded.|
|**ACID Transactions**|**No** (by default). Prone to data corruption/inconsistency.|**Yes.** Provides Atomicity, Consistency, Isolation, Durability.|**Yes.** Core feature of relational databases.|
|**Data Quality**|Low (raw, unfiltered). Can become a "data swamp."|High (due to ACID, schema enforcement, validation).|High (rigorous ETL processes ensure quality).|
|**Performance (BI/Analytics)**|Generally lower for complex queries on raw data. Requires external tools/engines.|Good to Excellent. Optimizations like data skipping, Z-ordering.|Excellent for predefined, structured queries.|
|**Cost**|Very Low (cheap object storage).|Low (builds on cheap object storage, but adds compute for features).|Higher (optimized for performance, often proprietary storage).|
|**Data Freshness**|Can be real-time or batch (raw ingestion).|Real-time and Batch processing on unified data.|Typically batch-oriented; less real-time by nature.|
|**Complexity**|High for management, governance, and finding usable data.|Moderate. Adds structure/governance, reducing "swamp" issues.|Moderate to High (complex ETL, fixed schema, scaling).|
|**Key Technologies/Formats**|Cloud Object Storage (S3, ADLS Gen2, GCS), HDFS, Parquet, ORC, JSON, CSV, text files, images.|**Delta Lake** (built on Parquet), Apache Spark.|Relational Database Management Systems (RDBMS), columnar stores (Redshift, Snowflake, BigQuery).|
|**Typical Users**|Data Scientists, Data Engineers (for raw data exploration).|Data Engineers, Data Scientists, BI Analysts (all on the same platform).|Business Analysts, BI Developers, Reporting Teams.|
|**Strengths**|Cost-effective for massive raw data; highly flexible.|Combines flexibility of Data Lake with reliability of Data Warehouse.|High performance for BI; strong data integrity and consistency.|
|**Weaknesses**|Lack of ACID, schema governance, query performance issues.|Still requires careful management and Spark/SQL knowledge.|Less flexible for unstructured data; higher cost; less ideal for ML on raw data.|

#### ACID (A.C.I.D.) = Rules for Reliable Data Changes**

1. **Atomicity (All or Nothing):**
    
    - **Simple:** Either everything in a transaction happens, or nothing happens. No half-finished changes.
        
    - **Analogy:** Sending money from A to B: Money either fully leaves A and lands in B, or it stays exactly in A. It never disappears in between.
        
2. **Consistency (Rules Followed):**
    
    - **Simple:** A transaction always keeps the data valid and follows all set rules.
        
    - **Analogy:** If a rule says "account balance can't be negative," a transaction that would make it negative will be stopped.
        
3. **Isolation (No Interference):**
    
    - **Simple:** Multiple transactions happening at the same time don't see or affect each other until they're complete.
        
    - **Analogy:** Two people buying the last concert ticket at the same time. Isolation ensures only one actually gets it, and the other sees it's gone.
        
4. **Durability (Permanent Save):**
    
    - **Simple:** Once a change is confirmed, it's saved forever, even if the system crashes.
        
    - **Analogy:** You save a document, and then your computer crashes. Durability means your changes are still there when you restart.

### Medallion Architecture Notes**

**Concept:** Data design pattern for data lakes/lakehouses, incrementally improving data quality & structure across layers.

---

**Layers:**

1. **Bronze Layer (Raw):**
    
    - **Purpose:** Store raw, immutable data as-is from source.
        
    - **Characteristics:** Unchanged, append-only, diverse formats, high volume.
        
2. **Silver Layer (Cleaned/Conformed):**
    
    - **Purpose:** Clean, validate, and standardize data. Integrate across sources.
        
    - **Characteristics:** Filtered, handled missing/duplicates, consistent format (often structured).
        
3. **Gold Layer (Curated/Business-Ready):**
    
    - **Purpose:** Store aggregated, optimized data for direct business use (BI, ML).
        
    - **Characteristics:** Summarized, analytical views, highly optimized for performance (e.g., Star Schema), business-specific.
      
![[Pasted image 20250628215718.png]]


![[Pasted image 20250628221325.png]]

### These clusters offer more control over underlying VMs and are managed by the user.

- **All-Purpose Clusters (Interactive Clusters):**
    
    - **Purpose:** Interactive analysis, collaborative development in notebooks.
        
    - **Lifecycle:** Manually created, started, terminated, restarted; persist until terminated.
        
    - **Use Cases:** Data exploration, ad-hoc queries, code development/testing, collaborative data science.
        
    - **Cost:** Billed for uptime (including idle time).
        
- **Job Clusters:**
    
    - **Purpose:** Automated jobs, production workloads; ephemeral.
        
    - **Lifecycle:** Automatically created by job scheduler when a job starts, terminated upon completion; cannot be manually restarted.
        
    - **Use Cases:** Scheduled ETL pipelines, batch processing, automated reporting, ML training jobs.
        
    - **Cost:** Billed only for active job run time.
        
- **High Concurrency Clusters:**
    
    - **Purpose:** Specialized All-Purpose Cluster for multiple concurrent users/queries (BI, interactive analytics).
        
    - **Characteristics:** Enhanced security, query-level isolation, fair resource allocation; often used with Unity Catalog.
        
    - **Use Cases:** BI dashboards, shared workspaces with many concurrent users.
        
- **Single Node Clusters:**
    
    - **Purpose:** Single Spark driver node (no workers); Spark runs in local mode.
        
    - **Characteristics:** All execution on one VM; suitable for smaller datasets.
        
    - **Use Cases:** Local development, testing on small samples, ML models not requiring distributed training.
        
- **GPU-Enabled Clusters:**
    
    - **Purpose:** Provisioned with GPUs for compute-intensive tasks.
        
    - **Characteristics:** Uses specific VM instance types with GPUs.
        
    - **Use Cases:** Deep learning model training, complex ML algorithms, high-performance computing.
    
    
## Unity catalog

- **What it is:** Databricks' central control system for all your data and AI assets. It's like a universal library catalog for your data lakehouse.
- **Purpose:** Ensures data is **secure, well-organized, auditable, and easy to find**. It brings data warehouse-like governance to your data lake
**Key Features:**
1. **Central Governance:** One place to manage access and rules for all data across your Databricks workspaces.
2. **`catalog.schema.table`:** Data is organized hierarchically: `Catalog` (big groups) > `Schema` (smaller groups/databases) > `Table` (your actual data).
3. **Easy Security:** Use standard SQL `GRANT`/`REVOKE` commands to control who can access what (down to columns/rows).
4. **Data Lineage:** Automatically tracks how data moves and changes, showing its origin and transformations.
5. **Auditing:** Records who accessed which data and when, for security and compliance.
6. **Data Discovery:** Helps users find data easily with search and tags.
7. **Managed vs. External:**
    - **Managed:** Unity Catalog controls both data and metadata (drops data when table is dropped).
    - **External:** Unity Catalog manages metadata/access; you manage the actual data files in your cloud storage (data stays if table dropped).
8. **Openness:** Works with open formats like Delta Lake; supports Delta Sharing for secure external data sharing.
9. **Simplifies Storage:** Manages secure connections to your cloud storage, no complex mount points needed.
![[Pasted image 20250628234634.png]]

## Databricks view types

Views are virtual tables on top of a result-set from an SQL query.

---

**Standard View (or Persistent View):**

- **Definition:** A view that's persisted on a schema/database in your Metastore (e.g. Unity Catalog or Hive Metastore).
    
- **Scope:** Enduring between sessions and between clusters. Stored as metadata.
    
- **Syntax:** `CREATE VIEW my_schema.my_view AS SELECT ...`
    
- **Use:** For reusable, shared logic or abstractions.
    

---

**Short-term Perspective (Temporary View):**

- **Definition:** A view that exists only for the lifespan of the SparkSession currently being used.
    
- **Scope:** Only accessible from notebook/session that it was generated on. Gets erased on session end.
    
- **Syntax:** `CREATE TEMPORARY VIEW my_temp_view AS SELECT ...`
    
- **Use:** For ad-hoc, rapid analysis or intermediate computation during a single session.
    

---

**Global Temporary View:**

- **Definition:** A view that exists across the entire Spark Application (cluster) on which it was created.
    
- **Scope:** Visible to any notebook/sessions that share the same Spark application (cluster). Deleted on termination of the cluster.
    
- **Syntax:** `CREATE GLOBAL TEMPORARY VIEW my_global_temp_view AS SELECT ...`
    
- **Access:** With a dedicated `global_temp` database: `SELECT * FROM global_temp.my_global_temp_view`
    
- **Use:** For transferring ephemeral, everyday datasets between multiple notebooks running on the same cluster.
    

---

**Materialized View (MV) / Streaming Table (Delta Live Tables - DLT):**

- **Definition:** They are those views whose result set is physically stored and refreshed periodically (materialized). They are tables from which the data is computed from a source query.
    
- **Scope:** Reserved data is permanently stored.
    
- **Characteristic:** The dataset is kept up-to-date automatically as the source data changes (batch or streaming).
    
- **Syntax (DLT):**
    
    - `CREATE OR REFRESH MATERIALIZED VIEW my_mv AS SELECT ...`
        
    - `CREATE OR REFRESH STREAMING TABLE my_streaming_table AS SELECT ...`
        
- **Use:** For query performance optimisation on complex/frequent queries, incrementally maintained aggregates, or building robust data pipelines (ETL/ELT).
  

### **How Spark Structured Streaming Loads Continuous Data into a Data Lake:**

1. **Continuous Source Reading:**
    
    - You configure a Structured Streaming job to **continuously read** from a source where new data arrives. This could be:
        
        - A **message queue** (like Apache Kafka, Azure Event Hubs, AWS Kinesis) that receives events in real-time.
            
        - A **directory in cloud object storage** (e.g., ADLS Gen2, AWS S3). Spark, especially with **Databricks Auto Loader**, can efficiently detect new files as they land in these directories.
            
        - A **Delta Lake table** itself, acting as a Change Data Feed (CDC) to stream changes (inserts, updates, deletes) from that table.
            
2. **Transformation (Optional but Common):**
    
    - As data is read in micro-batches, you can apply **any Spark DataFrame transformations** you need:
        
        - Schema enforcement or evolution.
            
        - Filtering out unwanted records.
            
        - Enriching data by joining with static (batch) tables.
            
        - Aggregations (e.g., counting events per minute).
            
        - Data quality checks and cleaning.
            
3. **Writing to a Data Lake Sink:**
    
    - The processed data is then continuously written to a designated location in your data lake. The most popular and recommended format for this is **Delta Lake**.
        
    - **Delta Lake** is crucial here because it brings ACID (Atomicity, Consistency, Isolation, Durability) transactions to your data lake. This is vital for streaming:
        
        - **Reliability:** Ensures that data is written completely and correctly, even if the stream fails.
            
        - **Concurrency:** Allows multiple streams or batch jobs to write to the same table simultaneously without corrupting data.
            
        - **Exactly-Once Processing:** Guarantees that each record is processed and written exactly once to the Delta Lake table, preventing duplicates.
            
4. **Checkpointing:**
    
    - Every Spark Structured Streaming job requires a **checkpoint location** (a path in your data lake).
        
    - Spark uses this to store the **state of the stream**, including which data it has already processed (e.g., Kafka offsets, file names processed).
        
    - If the streaming job stops or fails, it can restart from the last successful checkpoint, ensuring **fault tolerance and exactly-once delivery**. It knows exactly where it left off.
### **What is Auto Loader? (Quick Recap)**

**Auto Loader** is a Databricks feature that makes it easy and robust to **continuously load new data files** from your cloud storage (like ADLS Gen2, S3) into your Databricks Lakehouse.

It handles:

- **Automatic discovery** of new files.
    
- **Schema inference** (guessing column types).
    
- **Schema evolution** (adapting to changing data structure).
    
- **Exactly-once processing** (no duplicates or missed data, even on restarts).
    

Think of it as a smart, reliable conveyor belt that automatically brings new data files from your landing zone into your Delta Lake tables.
### **How to Use Auto Loader in SQL**

In Databricks, you can use Auto Loader directly within SQL by creating a **Streaming Table**. Streaming Tables are a feature of **Delta Live Tables (DLT)** or a standard Databricks SQL Warehouse that leverages Structured Streaming and Auto Loader under the hood.
**Example SQL Syntax:**
Let's assume you have JSON files landing in `abfss://rawdata@youradlsgen2.dfs.core.windows.net/events/`.

```
-- Create a streaming table that continuously ingests JSON files
-- using Auto Loader from a specified cloud storage location.

CREATE STREAMING TABLE raw_events_stream
AS SELECT *
FROM cloud_files(
  'abfss://rawdata@youradlsgen2.dfs.core.windows.net/events/', -- Your source cloud storage path
  'json',                                                       -- Format of the files
  map(                                                          -- Auto Loader options
    'cloudFiles.schemaLocation', 'abfss://checkpoints@youradlsgen2.dfs.core.windows.net/autoloader_schemas/raw_events_checkpoint/',
    'cloudFiles.inferSchema', 'true',                           -- (Optional) Automatically infer schema
    'cloudFiles.maxFilesPerTrigger', '1000'                     -- (Optional) Limit files per micro-batch
  )
);
```

## ==Delta Lake-==
	Delta Lake is the optimized storage layer that provides the foundation for tables in a Lakehouse on Databricks. Delta Lake is open source software that extends Parquet data files with a file-based transaction log for ACID transactions and scalable metadata handling.

![[{6F0E565C-20AE-4F5D-90AF-8DB6C895D149}.png]]

### **Delta Lake: Transaction Log & Time Travel**

**1. Transaction Log (Delta Log)**

- **What is it?**
    
    - The **heart** of a Delta Lake table.
        
    - An **ordered, atomic, append-only record** of _every change_ (transaction) to the table.
        
    - Physically, it's a series of **JSON files** (and compacted Parquet checkpoints) in a hidden `_delta_log` sub-directory within the table's path.
        
- **Use of it:**
    
    - **ACID Transactions:** Ensures reliability (all or nothing changes).
        
    - **Single Source of Truth:** Defines what data files belong to the table at any moment.
        
    - **Data Versioning:** Every successful write creates a new, numbered version of the table.
        
    - **Enables Time Travel:** The log is the foundation for accessing past versions.
        
    - **Concurrency Control:** Manages simultaneous reads/writes without corruption.
        
- **Example (Conceptual):**
    
    - `my_table/_delta_log/00000000000000000000.json` (Version 0 - Initial write)
        
    - `my_table/_delta_log/00000000000000000001.json` (Version 1 - Append)
        
    - `my_table/_delta_log/00000000000000000002.json` (Version 2 - Update/Delete, records old files removed, new files added)
        
- **Syntax: View History**
    
    - **SQL:**
        
        SQL
        
        ```
        DESCRIBE HISTORY your_delta_table_name;
        ```
        
    - **PySpark:**
        
        ```
        from delta.tables import DeltaTable
        delta_table = DeltaTable.forName(spark, "your_delta_table_name")
        delta_table.history().show()
        # Or if using path: DeltaTable.forPath(spark, "/path/to/table").history().show()
        ```
        
    - **Output shows:** `version`, `timestamp`, `operation`, `operationMetrics`, etc.

**2. Time Travel**

- **What is it?**
    
    - The ability to query or read a Delta Lake table as it existed at a **specific past version** or **timestamp**.
        
    - Leverages the historical information in the **Transaction Log**.
        
- **Use of it:**
    
    - **Reproducibility:** Re-run analyses or models on historical data.
        
    - **Auditing:** See how data has changed over time.
        
    - **Error Recovery:** Quickly fix bad writes by retrieving a good past version.
        
    - **As-of Queries:** Analyze data based on a past state.
        
- **Syntax: Query Past Versions**
    
    **a) By Version Number:**
    
    - **SQL:**
        
        SQL
        
        ```
        SELECT *
        FROM sales_data VERSION AS OF 2; -- Query version 2
        
        -- Shorthand
        SELECT *
        FROM sales_data@v2;
        ```
        
    - **PySpark:**
        
        Python
        
        ```
        df_version_2 = spark.read \
                             .format("delta") \
                             .option("versionAsOf", 2) \
                             .load("/path/to/sales_data_table")
        df_version_2.show()
        ```
        
    
    **b) By Timestamp:**
    
    - **SQL:**
        
        SQL
        
        ```
        SELECT *
        FROM sales_data TIMESTAMP AS OF '2025-06-25 10:00:00'; -- Query as of a specific time
        
        -- Shorthand (YYYYMMDDHHmmssSSS format)
        SELECT *
        FROM sales_data@20250625100000000;
        ```
        
    - **PySpark:**
        
        Python
        
        ```
        df_as_of_time = spark.read \
                              .format("delta") \
                              .option("timestampAsOf", "2025-06-25 10:00:00") \
                              .load("/path/to/sales_data_table")
        df_as_of_time.show()
        ```
        
- **Impact of `VACUUM` on Time Travel:**
    
    - The `VACUUM` command **physically deletes old data files** that are no longer referenced by the transaction log and are older than a defined **retention period** (default 7 days).
        
    - **Running `VACUUM` will limit your ability to time travel** to versions older than the specified retention period, as the underlying data files might be removed from storage.
        
    - **Syntax (`VACUUM`):**
        
        SQL
        
        ```
        -- SQL: Remove files older than 7 days (default retention)
        VACUUM your_delta_table_name;
        
        -- SQL: Remove files older than 24 hours
        VACUUM your_delta_table_name RETAIN 24 HOURS;
        
        -- SQL: See what files would be deleted without actually deleting them
        VACUUM your_delta_table_name DRY RUN;
        ```

**3. RESTORE Command (Reverting a Table)**

- **What it is:** The `RESTORE` command allows you to **revert a Delta Lake table to a previous version or timestamp**.
    
- **Key Concept:** When you `RESTORE`, it doesn't delete the history or simply "go back" in time. Instead, it **creates a new transaction (a new version)** in the Delta Log that makes the table's _current state_ identical to the specified past version or timestamp.
    
- **Use of it:**
    
    - **Recover from Errors:** The primary use case is to quickly recover from accidental data deletions, updates, or bad data loads.
        
    - **Rollback:** Effectively "undo" a series of changes to your table.
        
- **Syntax: Revert Table State**
    
    **a) Restore by Version Number:**
    
    - **SQL:**
        ```
        -- Restore the 'sales_data' table to the state it was at version 2
        RESTORE TABLE sales_data TO VERSION AS OF 2;
        ```
    - **PySpark:**
        ```
        from delta.tables import DeltaTable
        
        # Load the DeltaTable object
        delta_table = DeltaTable.forName(spark, "sales_data")
        # Or, if using path: delta_table = DeltaTable.forPath(spark, "/path/to/your/delta/table/sales_data")
        
        # Restore to version 2
        delta_table.restoreToVersion(2)
        ```
    **b) Restore by Timestamp:**
    
    - **SQL:**
        ```
        -- Restore the 'sales_data' table to the state it was at a specific timestamp
        -- Use an actual timestamp from your history, e.g., '2025-06-25 10:00:00'
        RESTORE TABLE sales_data TO TIMESTAMP AS OF '2025-06-25 10:00:00';
        ```
        
    - **PySpark:**
        ```
        from delta.tables import DeltaTable
        
        delta_table = DeltaTable.forName(spark, "sales_data")
        # Restore to the state as of the given timestamp
        delta_table.restoreToTimestamp("2025-06-25 10:00:00")
        ```

## DLT
DLT stands for Delta Live Tables.  
It's a tool inside Databricks, built on Spark and Delta Lake.  
It helps you build reliable and testable data pipelines.

You just tell it what tables you want and how to transform the data — it takes care of the rest.

**Why use it?**

- **Simple ETL/ELT**: Use SQL or Python to define your pipeline.
    
- **Auto Infrastructure**: DLT handles cluster setup, scaling, and table order.
    
- **Data Quality Built-In**:
    
    - Use “expectations” to set data rules.
        
    - If data breaks rules, it can be dropped, quarantined, or stop the pipeline.
        
    - Easy to monitor through the built-in UI.
        
- **Incremental Updates**: Handles new/streaming data efficiently.
    
- **Error Handling**: DLT retries jobs and handles failures automatically.
    
- **Testing**: Expectations help check data quality during testing.

**Key Terms:**

- **Declarative**: You describe the final result, not each step.
    
- **Pipelines**: A group of related tables.
    
- **Live Tables**: Tables created by DLT (batch or streaming).
    
- **Expectations**: Rules for your data.
    
- **CREATE LIVE TABLE**: SQL command to make a table in DLT.

**In short**:  
DLT makes building data pipelines easier by taking care of infrastructure, monitoring, and errors so you can focus on the data.

![[{CBD390DA-7112-4E90-847D-3A829F22B533}.png]]

![[{B0A3DCBB-B1B1-4B3D-91E5-402FF71A3741}.png]]

