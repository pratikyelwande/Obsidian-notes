# ==Interview Questions Prep==
## Different Types of SQL JOINs

Here are the different types of the JOINs in SQL:

- `(INNER) JOIN`: Returns records that have matching values in both tables
- `LEFT (OUTER) JOIN`: Returns all records from the left table, and the matched records from the right table
- `RIGHT (OUTER) JOIN`: Returns all records from the right table, and the matched records from the left table
- `FULL (OUTER) JOIN`: Returns all records when there is a match in either left or right table

![SQL INNER JOIN](https://www.w3schools.com/sql/img_inner_join.png)  ![SQL LEFT JOIN](https://www.w3schools.com/sql/img_left_join.png)  
![SQL RIGHT JOIN](https://www.w3schools.com/sql/img_right_join.png)  ![SQL FULL OUTER JOIN](https://www.w3schools.com/sql/img_full_outer_join.png)



## **Relational Database vs RDBMS**

| Feature            | **Relational Database**                                                                    | **RDBMS (Relational Database Management System)**                                                         |
| ------------------ | ------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------- |
| 🔧 **Definition**  | A _relational database_ is a **concept** or **design** that stores data in related tables. | RDBMS is a **software/system** that allows you to manage, access, and interact with relational databases. |
| 🏗️ **What it is** | A **structure** or model (like an idea)                                                    | A **tool** or application (like a program)                                                                |
| 📦 **Storage**     | Just the **data in tabular form** (rows and columns)                                       | Stores the data + provides **tools** to query, update, manage users, and enforce security                 |
### **1. What is SQL? List its types.**

**SQL (Structured Query Language)** is a standard language used to interact with relational databases. It allows users to **create**, **read**, **update**, and **delete** (CRUD) data.

**Types of SQL Statements:**

- **DDL** (Data Definition Language): `CREATE`, `ALTER`, `DROP`, `TRUNCATE`
    
- **DML** (Data Manipulation Language): `INSERT`, `UPDATE`, `DELETE`
    
- **DQL** (Data Query Language): `SELECT`
    
- **DCL** (Data Control Language): `GRANT`, `REVOKE`
    
- **TCL** (Transaction Control Language): `COMMIT`, `ROLLBACK`, `SAVEPOINT`
  
### **What is a Constraint? Types of Constraints**

**Constraints** are rules enforced on data columns to ensure data integrity.

**Types:**

- `NOT NULL`: Prevents NULL values.
    
- `UNIQUE`: Ensures all values in a column are different.
    
- `PRIMARY KEY`: Combines `NOT NULL` and `UNIQUE`.
    
- `FOREIGN KEY`: Enforces relationship between tables.
    
- `CHECK`: Validates data against a condition.
    
- `DEFAULT`: Sets a default value.

### **Difference between DELETE, TRUNCATE, and DROP**

|Command|Removes|Can Use WHERE|Rollback|Resets Identity|
|---|---|---|---|---|
|`DELETE`|Specific rows|Yes|Yes|No|
|`TRUNCATE`|All rows|No|No|Yes|
|`DROP`|Entire table|No|No|N/A|
### **What is ACID in SQL?**

ACID refers to the **four key properties** that ensure **reliable transactions** in a database:

| Property            | Description                                                              |
| ------------------- | ------------------------------------------------------------------------ |
| **A - Atomicity**   | All operations in a transaction are done or none (all-or-nothing)        |
| **C - Consistency** | Data must always be in a valid state before and after a transaction      |
| **I - Isolation**   | Multiple transactions should not interfere with each other               |
| **D - Durability**  | Once a transaction is committed, it is saved permanently—even in a crash |
|                     |                                                                          |
### **What are Triggers?**

A **trigger** is a **special stored procedure** that **automatically runs** when an event (like `INSERT`, `UPDATE`, or `DELETE`) occurs on a table.

