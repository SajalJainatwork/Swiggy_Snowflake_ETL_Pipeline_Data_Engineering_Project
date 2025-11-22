# 🍽 Swiggy Data Engineering Project (Snowflake + Streamlit)

An end-to-end data engineering project built using **Snowflake** (via Web UI) and a **Streamlit dashboard** for visualizing Swiggy order insights.  
This project demonstrates data ingestion, transformation, aggregation, and visualization — fully in the cloud.

---

## 📌 Project Overview
- **Data Source:** Raw CSV order data (`data/` folder)  
- **Data Warehouse:** Snowflake (Web UI workflow)  
- **Transformation:** SQL scripts in `transformations/`  
- **Visualization:** Streamlit dashboard in `dashboard/`  
- **Goal:** Provide fast, interactive KPIs and trends from Swiggy order data.

---
![1_jy2bD71HdevMHO1G_F_d-w](https://github.com/user-attachments/assets/dd92d3f0-ed9f-4a3d-a634-b9bf37a1d012)


## ⚙️ Setup Instructions

### 1️⃣ Prepare Snowflake environment
- Create **three schemas** in your database:
  - `STAGING` – for raw ingested data
  - `CLEAN` – for cleaned and standardized data
  - `CONSUMPTION` – for aggregated analytics

---

### 2️⃣ Load raw data
- In Snowflake Web UI, create tables in `STAGING` matching the raw CSV structure.
- Upload CSV files from the `data/initial` & `data/delta` folder using Snowflake’s **Load Data** option.
- Keep data unaltered at this stage for auditing and backup.

---

### 3️⃣ Apply transformations
- **Clean Layer**  
  - Create tables in `CLEAN` schema using `/clean_stg`  
  - Standardize formats, remove duplicates, handle nulls, join reference data  
  - Implement incremental loading to process only new/updated rows  
- **Consumption Layer**  
  - Create aggregated tables using `/consumption_stg`  
  - Pre-compute KPIs such as total revenue, total orders, max order value

---

### 4️⃣ Connect Streamlit
- Update `dashboard/app.py` with your Snowflake account details.
- Streamlit will query the `CONSUMPTION` schema for fast results.

---

## 🔄 Pipeline Stages

### **1. Staging Layer**
- Stores raw ingested data exactly as received.
- Acts as a secure backup for reprocessing and compliance.

### **2. Clean Layer**
- Produces analytics-ready data by cleaning, standardizing, and enriching.
- Handles duplicates, nulls, and type mismatches.

### **3. Consumption Layer**
- Stores aggregated, query-optimized tables.
- Pre-calculated KPIs improve dashboard responsiveness.

---

## 📊 Dashboard
- Built with **Streamlit** and connected directly to Snowflake.
- Displays:
  - Total Revenue
  - Total Orders
  - Max Order Value
  - Trends over time
- Uses pre-aggregated data for minimal latency.

---
<img width="3840" height="2160" alt="SWIGGY Data Pipeline _ End To End Data Engineering Project In Snowflake 1-53-23 screenshot" src="https://github.com/user-attachments/assets/41d32544-40ab-4d66-b9e8-6efa2e468156" />
