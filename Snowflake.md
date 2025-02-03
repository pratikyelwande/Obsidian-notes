## Snow-pro core

![[Ultimate_SnowPro_Core_Certification_Course_Slides_by_Tom_Bailey.pdf]]
## Syllabus

### **1.0 Snowflake AI Data Cloud Features & Architecture (24%)**

1. **Key Features of Snowflake:**
    
    - **Separation of Storage and Compute:** Independent scaling for performance and cost efficiency.
    - **Multi-cluster Shared Data Architecture:** Supports concurrent users without performance degradation.
    - **Cloud-Agnostic:** Runs on AWS, Azure, and GCP.
    - **Data Types:** Supports structured, semi-structured (JSON, Parquet, etc.), and unstructured data.
    - **Micro-Partitions:** Automatically divided storage for efficient querying.
    - **Time Travel:** View historical data for a specified retention period (up to 90 days).
2. **Components:**
    
    - **Virtual Warehouses:** Compute clusters for processing queries.
    - **Storage Layer:** Scalable and compressed data storage.
    - **Cloud Services Layer:** Handles metadata, security, and transaction management.
3. **Clustering:**
    
    - **Automatic Clustering:** No need for manual index management.
    - **Search Optimization Service:** Improves query performance on selective queries.
4. **Caching Layers:**
    
    - **Result Cache:** Stores results of executed queries.
    - **Metadata Cache:** Stores schema and statistics.
    - **Local Disk Cache:** Improves performance of repeated queries.

---

### **2.0 Account Access and Security (18%)**

1. **Access Management:**
    
    - **Authentication:** Supports SSO, MFA, and OAuth.
    - **RBAC (Role-Based Access Control):** Uses roles like ACCOUNTADMIN, SYSADMIN, PUBLIC.
    - **Policies:** Enforce password complexity, IP whitelisting, and session settings.
2. **Security Features:**
    
    - **Encryption:** End-to-end encryption for data at rest and in transit.
    - **Network Policies:** Restrict access to IP ranges or cloud services.
    - **Private Connectivity:** Direct access using AWS PrivateLink or Azure Private Link.
    - **Audit Logging:** Tracks access and queries for compliance.

---

### **3.0 Performance and Cost Optimization Concepts (16%)**

1. **Performance Optimization:**
    
    - Use **Virtual Warehouse Scaling:** Scale vertically (size) or horizontally (multi-cluster).
    - **Query Profiling:** Use `EXPLAIN` and Query History to identify bottlenecks.
    - Optimize **Data Clustering** and **Search Optimization Service.**
2. **Cost Management:**
    
    - Use **Auto-Suspend/Resume** for warehouses.
    - Monitor usage with the **Account Usage** schema.
    - Optimize storage with columnar compression and by purging unused data.
3. **Resource Monitoring:**
    
    - Use **Resource Monitors** to set credit usage limits.
    - Analyze **Query History** to identify long-running queries.

---

### **4.0 Data Loading and Unloading (12%)**

1. **Data Loading Methods:**
    
    - **Stages:** Temporary storage areas for bulk loading (`INTERNAL`, `EXTERNAL`, or `USER` stages).
    - **Snowpipe:** Continuous data ingestion with automated triggers.
    - **COPY Command:** Load bulk data efficiently.
2. **Data Unloading:**
    
    - Use the **`COPY INTO`** command to export data.
    - Supports unloading into formats like **CSV**, **JSON**, and **Parquet**.
3. **Helper Commands:**
    
    - `LIST`: Lists files in a stage.
    - `REMOVE`: Deletes files from a stage.
    - `GET`: Downloads files from a stage.

---

### **5.0 Data Transformations (18%)**

1. **SQL Support:**
    
    - Full support for ANSI SQL.
    - Functions for structured (`SUM`, `GROUP BY`) and semi-structured data (`OBJECT_INSERT`, `ARRAY_AGG`).
2. **Stored Procedures & UDFs:**
    
    - **JavaScript Stored Procedures:** Encapsulate complex logic.
    - **User-Defined Functions (UDFs):** Create custom reusable SQL functions.
3. **Stream and Task Automation:**
    
    - **Streams:** Track changes in tables for incremental transformations.
    - **Tasks:** Automate data transformation workflows.

---

### **6.0 Data Protection and Data Sharing (12%)**

1. **Data Protection:**
    
    - **Time Travel:** Recover data to previous states within retention periods.
    - **Fail-safe:** Additional recovery mechanism (7 days post-Time Travel).
    - **Encryption:** Built-in for data at rest and in transit.
2. **Data Sharing:**
    
    - **Secure Data Sharing:** Share data without copying via Reader Accounts.
    - **Data Marketplace:** Publish data for discovery and sharing.
    - **Private Data Exchange:** Collaborative sharing for approved participants.

#### 1.0 **Key Features of Snowflake**

1. **Separation of Storage and Compute:**
    
    - Compute (Virtual Warehouses) and Storage scale independently.
    - Enables efficient resource utilization and cost savings.
2. **Multi-Cluster Shared Data Architecture:**
    
    - Allows multiple users or workloads to query the same data simultaneously without impacting performance.
    - Ensures concurrency with consistent query performance.
3. **Cloud-Agnostic Platform:**
    
    - Available on AWS, Azure, and Google Cloud.
    - Supports multi-cloud deployments and replication.
4. **Data Support:**
    
    - **Structured Data:** Tables and schemas.
    - **Semi-structured Data:** JSON, Parquet, Avro, ORC.
    - **Unstructured Data:** Images, videos, PDFs, etc., stored in `STAGE`.
5. **Time Travel:**
    
    - View and query historical data for a retention period of up to **90 days**.
    - Supports recovery from accidental changes or deletions.
6. **Zero-Copy Cloning:**
    
    - Create clones of databases, schemas, or tables without duplicating data.
    - Changes to clones do not affect the original object.
7. **Data Sharing:**
    
    - Share data in real-time without copying or moving it.
    - Secure data sharing with external accounts using **Reader Accounts** or **Data Exchange**.
8. **Search Optimization Service:**
    
    - Improves performance for selective queries on large datasets by optimizing columnar data access.

--- 

### Snowflake architecture
![[Pasted image 20250116093832.png]]
### **1. Storage Layer**

This layer is responsible for storing all data in a **centralized and compressed columnar format**.

- **Features:**
    - **Micro-Partitions:**  
        Data is divided into small chunks called micro-partitions (50–500 MB in size), enabling efficient storage and retrieval.
    - **Metadata Management:**  
        Stores information about data location, statistics, and structure for fast query performance.
    - **Cloud-Agnostic:**  
        Works on AWS, Azure, and Google Cloud.
    - **Immutable Storage:**  
        Ensures data integrity by making stored data read-only and versioned.
    - **Support for All Data Types:**  
        Handles structured, semi-structured (JSON, Avro, ORC, Parquet), and unstructured data (images, videos).

---

### **2. Compute Layer (Virtual Warehouses)**

This layer handles all query processing and computation. It is made up of **independent compute clusters** called virtual warehouses.

- **Features:**
    - **Independent Scaling:**  
        Virtual warehouses can scale up (add resources to a cluster) or out (add more clusters) independently.
    - **Concurrency Scaling:**  
        Automatically adds compute clusters when demand increases, avoiding performance bottlenecks.
    - **Query Execution:**  
        Handles tasks like joins, aggregations, and filtering.
    - **Local Disk Caching:**  
        Stores frequently accessed data temporarily to improve performance.
    - **Multi-Cluster Warehouses:**  
        Enables automatic load balancing for concurrent queries.

---

### **3. Cloud Services Layer**

The **brain** of the Snowflake architecture. It coordinates activities between the storage and compute layers.

- **Features:**
    - **Query Optimization:**  
        Automatically generates optimal execution plans for queries.
    - **Metadata Management:**  
        Maintains metadata for efficient query execution (e.g., schema, data locations).
    - **Security and Access Control:**  
        Implements authentication, encryption, and role-based access control (RBAC).
    - **Transaction Management:**  
        Ensures **ACID compliance** and supports features like time travel.
    - **Result Caching:**  
        Returns cached query results instantly to reduce compute costs for repeated queries.

### **What is Snowflake?**

Snowflake is a **cloud-based data platform** that provides a unified solution for data storage, processing, and analytics. It is designed to work seamlessly across multiple cloud providers (**AWS, Azure, and Google Cloud**) and offers unique features to handle structured, semi-structured, and unstructured data efficiently.

### **Comparison with Other Architectures**

| Feature                 | Shared Disk Architecture           | Shared Nothing Architecture       |
| ----------------------- | ---------------------------------- | --------------------------------- |
| **Storage**             | Centralized                        | Distributed across nodes          |
| **Compute**             | Nodes share compute resources      | Nodes are completely independent  |
| **Scalability**         | Limited by shared storage          | High scalability with added nodes |
| **Resource Contention** | High                               | None (no shared resources)        |
| **Fault Tolerance**     | Limited (shared resources failure) | High (independent nodes)          |
### **Storage Layer in Snowflake**

The **Storage Layer** is one of the foundational components of Snowflake's architecture. It handles all data storage responsibilities and provides a highly scalable, secure, and efficient environment. Here's a breakdown of its functionality and design:

---

### **1. Core Functions of the Storage Layer**

- **Data Storage**: Snowflake stores data in a columnar format, optimized for analytics and querying.
- **Separation from Compute**: Storage is completely independent of compute, allowing for dynamic scaling and efficient resource usage.
- **Immutable Micro-Partitions**: Data is divided into small, immutable blocks (micro-partitions) for efficient management and querying.
- **Automatic Compression**: Data is automatically compressed to minimize storage costs.

---

### **2. Key Features**

- **Cloud-Based**: Snowflake uses cloud object storage (e.g., Amazon S3, Azure Blob Storage, Google Cloud Storage) for durability and scalability.
- **Automatic Optimization**: Data is organized and maintained automatically without manual intervention.
- **Data Encryption**: All data is encrypted, ensuring security at rest and in transit.
- **Time Travel and Fail-Safe**:
    - **Time Travel**: Enables querying historical data for a specified period (e.g., 1-90 days).
    - **Fail-Safe**: Provides an additional 7-day window to recover data after the Time Travel period.

---

### **3. Components of the Storage Layer**

- **Micro-Partitions**:
    - Data is stored in **columnar format** and divided into micro-partitions (50–500 MB).
    - Each micro-partition is automatically indexed with metadata for efficient querying.
- **Metadata Repository**:
    - Tracks information about the micro-partitions, like row counts, min/max values, and distribution of data.
    - Facilitates query optimization by pruning irrelevant micro-partitions.
- **Cloud Object Storage**:
    - Data is stored redundantly across multiple locations for durability and availability.

### What is Query Processing?

Query processing is the work Snowflake does to understand, execute, and return results for your SQL queries. This happens in the **Compute Layer**, which consists of virtual warehouses.

### Cloud Services Layer in Snowflake

The **Cloud Services Layer** is the brain of Snowflake's architecture. It handles all the "management" tasks that keep the platform running smoothly. This layer doesn't process the data directly but ensures that everything works efficiently.

---

### **What Does the Cloud Services Layer Do?**

1. **Query Parsing and Optimization**
    
    - Checks if your SQL query is valid (syntax and structure).
    - Plans the most efficient way to execute the query (e.g., choosing indexes or partitions).
2. **Metadata Management**
    
    - Keeps track of all your data: tables, schemas, columns, and files.
    - Tracks where data is stored and how it's structured in the **Storage Layer**.
3. **Authentication and Access Control**
    
    - Manages user accounts and security.
    - Ensures only authorized users can access data and resources.
4. **Resource Management**
    
    - Allocates compute resources (virtual warehouses) for running your queries.
    - Scales resources up or down based on demand.
5. **Transaction Management**
    
    - Supports **ACID transactions** to ensure data consistency.
    - Handles concurrent queries without conflicts.
6. **Result Caching**
    
    - Stores query results for faster retrieval when the same query is run again.
7. **Data Governance**
    
    - Supports features like data masking, row access policies, and auditing.
    - Ensures compliance with data privacy regulations.

# Table types
### **1. Permanent Table**

- **Description**:
    - A standard table type used for persistent storage of data.
    - The data in these tables remains until explicitly deleted.
    - Data is stored in **Snowflake-managed storage** and benefits from features like replication and time travel.
- **Use Case**:
    - For long-term storage of critical data that needs to be retained and queried regularly.
- **Key Features**:
    - Supports **Time Travel** (1 to 90 days depending on the edition).
    - Can be cloned or restored.

---

### **2. Temporary Table**

- **Description**:
    - A table that exists only for the duration of a session.
    - Data is automatically dropped at the end of the session, and no recovery options are available.
- **Use Case**:
    - For session-specific or intermediate calculations and transformations.
    - Suitable for staging data that is not needed after the session ends.
- **Key Features**:
    - Does not support **Time Travel** or cloning.
    - Not visible to other sessions.

---

### **3. Transient Table**

- **Description**:
    - A table similar to a permanent table but with lower costs.
    - Does not support **Time Travel** or data retention after being dropped.
- **Use Case**:
    - For temporary or less critical data where cost savings are a priority.
    - Data that does not require point-in-time recovery.
- **Key Features**:
    - Faster deletion (no data retention for Time Travel).
    - Ideal for staging or interim processing.

---

### **4. External Table**

- **Description**:
    - A table that references data stored in external cloud storage (e.g., AWS S3, Azure Blob Storage, Google Cloud Storage).
    - Allows querying external data without loading it into Snowflake.
- **Use Case**:
    - For data stored outside Snowflake that needs to be queried or combined with data in Snowflake.
    - Useful for cost-effective access to large, infrequently queried datasets.
- **Key Features**:
    - Read-only access to external data.
    - Requires defining an external stage.


---

### Comparison Table:

|Feature|Permanent Table|Temporary Table|Transient Table|External Table|
|---|---|---|---|---|
|**Persistence**|Persistent|Session-only|Persistent|External (Read-only)|
|**Time Travel**|Yes|No|No|No|
|**Cost**|Standard|Low|Low|Storage-only|
|**Use Case**|Long-term data|Session tasks|Interim tasks|Query external data|
# View 
### 1. **Standard View**

A standard view in Snowflake is simply a stored query that you can use as if it were a table. The data in the view is not physically stored; it is computed each time the view is queried.

- **Creation**:
    
    sql
    `CREATE VIEW view_name AS SELECT column1, column2 FROM table_name WHERE condition;`
    
- **Use Case**: Use for abstracting business logic, simplifying complex queries, or restricting access to certain columns or rows.
    

### 2. **Materialized View**

A **materialized view** in Snowflake is a type of view that stores the results of the query in a physical storage location, which is periodically refreshed. Unlike standard views, which are computed at query time, materialized views provide precomputed results that can improve performance for large datasets.

- **Creation**:
    
    sql
    `CREATE MATERIALIZED VIEW view_name AS SELECT column1, column2 FROM table_name WHERE condition;`
    
- **Use Case**: Materialized views are typically used for improving performance on large and complex queries, especially for frequently run reporting or analytical queries.
    
- **Refresh**: Materialized views in Snowflake are automatically refreshed when the underlying data changes. However, you can also manually refresh them.
    
    sql
    
    `ALTER MATERIALIZED VIEW view_name REFRESH;`
    

### 3. **Secure View**

A **secure view** is a type of view that ensures the underlying query cannot be exposed by users with certain access privileges. The data is protected, and the view itself is more secure, ensuring that sensitive information is handled securely.

- **Creation**:
    
    sql
    `CREATE SECURE VIEW view_name AS SELECT column1, column2 FROM table_name WHERE condition;`
    
- **Use Case**: Secure views are used for sensitive or regulated data where you need to prevent access to the underlying query, providing an additional layer of security.

# Snowflake Scripting
**1. Cursor** is a database object used to retrieve and process query results one row at a time. Cursors are primarily used in **stored procedures** to handle complex query results and allow you to iterate over them row by row.

2.  Result set - When you run a query in Snowflake (or any database), the database processes the query and gives you a **table of data** as output

### Summary of Privileges:

|**Role**|**Key Responsibilities**|**Access Scope**|
|---|---|---|
|**USERADMIN**|Manage user accounts and role assignments|No data access, focuses on user and role management|
|**SECURITYADMIN**|Manage roles, grants, and privileges|No data access, focuses on security and role management|
|**SYSADMIN**|Manage databases, schemas, and data objects (except user roles)|Can access data, manage schemas, databases, and objects|
|**ACCOUNTADMIN**|Full administrative control over account and all Snowflake operations|Full access to all aspects of the Snowflake environment, including billing and account configuration|

### Role Hierarchy:

- **ACCOUNTADMIN** has all the powers of **SYSADMIN**, **SECURITYADMIN**, and **USERADMIN** roles.
- **SYSADMIN** has all the powers of **SECURITYADMIN** and **USERADMIN** but not **ACCOUNTADMIN**'s full access.
- **SECURITYADMIN** has all the powers of **USERADMIN** but does not have data management access.
- **USERADMIN** has the least privileges, focusing on user and role management.

|**Aspect**|**Encryption at Rest**|**Encryption in Transit**|
|---|---|---|
|**Definition**|Encryption of data while stored in databases, disks, or storage|Encryption of data while it is being transmitted over a network|
|**Purpose**|Protect stored data from unauthorized access|Prevent data interception or alteration during transmission|
|**Encryption Standard**|AES-256 encryption (for data storage)|TLS/SSL encryption (for data transfer)|
|**Scope**|Data stored on cloud or physical media|Data being transmitted (e.g., client-server, cloud communication)|
|**Managed By**|Managed by Snowflake (with optional BYOK)|Managed by Snowflake’s servers and client configuration|
|**Example in Snowflake**|Encrypted data in Snowflake storage|Encrypted connections between Snowflake clients and servers|
### **Concurrency Behavior Properties Overview**

#### **1. Statement Timeout in Seconds**

- **Definition**: Limits the maximum time a query can **execute** before being automatically terminated.
- **Purpose**: Prevents long-running queries from monopolizing resources.
- **How to Set**:
    - At session level:
        
        sql
        `ALTER SESSION SET STATEMENT_TIMEOUT_IN_SECONDS = <value>;`
        
    - At warehouse level:
        
        sql
        `ALTER WAREHOUSE my_warehouse SET STATEMENT_TIMEOUT_IN_SECONDS = <value>;`
        

#### **2. Statement Queued Timeout in Seconds**

- **Definition**: Limits how long a query can **wait in the execution queue** before being canceled.
- **Purpose**: Ensures that queries stuck in a queue for too long don't hold up workflows.
- **How to Set**:
    - At session level:
        
        sql
        `ALTER SESSION SET STATEMENT_QUEUED_TIMEOUT_IN_SECONDS = <value>;`
        
    - At warehouse level:
        
        sql
        `ALTER WAREHOUSE my_warehouse SET STATEMENT_QUEUED_TIMEOUT_IN_SECONDS = <value>;`
        

#### **3. Max Concurrency Level**

- **Definition**: Specifies the **maximum number of queries** a warehouse can execute concurrently.
- **Purpose**: Controls workload management and resource allocation.
- **Default Value**: Depends on the size of the warehouse. Larger warehouses can handle more concurrent queries.
- **How to Set**:
    
    sql
    `ALTER WAREHOUSE my_warehouse SET MAX_CONCURRENCY_LEVEL = <value>;`


