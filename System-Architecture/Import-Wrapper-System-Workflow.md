# Import Wrapper System – Overall Workflow

The **Import Wrapper System** is a unified solution used to import data feeds received in an **SFTP location** into the **target database server** through a **staging server**.  
The staging server is used to materialize the data and perform **standard and business validations** before the data is inserted into the target tables.

---

## Overview

- The import system requires **multi-step processing across multiple servers** to import the feeds received from the client into the target tables.
- Data is **not imported directly** from the data source into the target database.
- Each step in the process performs a **specific task or set of tasks** to ensure data quality and integrity.
- The diagram below illustrates the **overall workflow of the import process**.

<p align="center">
<img src="INSERT_DIAGRAM_LINK_HERE" width="900">
</p>

---

## Import Workflow Steps

At a high level, the **Import Wrapper process** involves the following steps:

### 1. File Received in SFTP Server
The client sends the data feed file, which is received and stored in the **SFTP server**.

---

### 2. File Transfer to Staging Server
The **Mover system** monitors the SFTP location, picks up the file, and transfers it to the **staging server**.

---

### 3. Preprocessing
Preprocessing tasks are performed on the file before loading the data. These include:

- File decryption
- Data preprocessing using **AWK scripts**

---

### 4. Data Loading into Staging Table
The processed data is loaded into a **staging table**.

- The staging table is designed as a **generalized feed table**.
- It can handle **multiple feed types within a single table structure**.

---

### 5. Standard Data Validation
Data is materialized in order to perform **standard validations**.

If the data passes these checks, it is forwarded to an **intermediate area in the target server**.

---

### 6. Business Rule Validation
Further validations are performed based on **specific business rules**.

- Validations are performed **row by row**.
- Rows that fail validation may be **flagged**.
- Warning messages may also be generated for certain conditions.

Performing validations before import reduces the likelihood of **import failures in later stages**.

---

### 7. Data Transformation and Candidate Table Load
The **import process transforms the data** and loads it into **candidate tables**.

- Candidate tables mirror the structure of the **target tables**.
- Data cleansing and transformation ("data massage") occurs at this stage to prepare the data for insertion or update.

---

### 8. Validation Reporting
Validation results are sent back to the **staging server**, where a **validation summary report** is generated.

The report provides:

- Summary of validation results
- Records that failed validation
- Warning messages generated during processing

This report helps in identifying and resolving **data quality issues before final data integration**.
