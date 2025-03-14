### 📌 DBT-Kestra-ETL Project 

#### **🚀 Overview**  
The **DBT-Kestra-ETL** project automates the **end-to-end data pipeline**, leveraging **Kestra** for data ingestion and **dbt** (Data Build Tool) for transformations in **Google BigQuery**.  

### **Architecture** 🏛️  
1️⃣ **Kestra Flows** handle:  
   - Extracting data from sources 📂  
   - Loading data into **BigQuery** 🎯  
   - Syncing dbt project files from GitHub 🔄  

2️⃣ **dbt Cloud** handles:  
   - **Scheduled transformations** (daily, CI/CD) ⏳  
   - **Data modeling & testing** 🧪  

---

### **⚙️ Workflow Breakdown**  

#### **1️⃣ Data Ingestion & Loading with Kestra**
- **Kestra flows** extract raw data from various sources.  
- The extracted data is loaded into **Google BigQuery** for further processing.  

#### **2️⃣ Data Transformation with dbt**
- **dbt manages all transformations in BigQuery**, including:  
  - **Cleaning, joining, and aggregating raw data** into analytical tables.  
  - **Creating materialized views and models** for optimized queries.  
  - **Running tests to validate data integrity**.  

#### **3️⃣ dbt Scheduling & CI/CD**
✅ **First of the Month:** dbt automatically **executes transformations every first of the month** to update the veiws and analytical tables .  
✅ **CI/CD Pipeline:** dbt runs **on every push to the main branch**, ensuring that transformations are always up-to-date.  
✅ **Documentation & Testing:** dbt generates data documentation and runs quality checks.  

---

### **🔄 Automation Flow**  

#### **📌 Kestra Flow for Data Ingestion**
Handles **data extraction and loading** into BigQuery.    
```yaml
triggers:
  - id: green_schedule
    type: io.kestra.plugin.core.trigger.Schedule
    cron: "0 5 1 * *"
    inputs:
      taxi: green

  - id: yellow_schedule
    type: io.kestra.plugin.core.trigger.Schedule
    cron: "0 6 1 * *"
    inputs:
      taxi: yellow
```
- Runs **Green Taxi dbt models** at **5 AM** on the **1st of the month**.  
- Runs **Yellow Taxi dbt models** at **6 AM** on the **1st of the month**.

---

### **🚀 Technologies Used**
- **Kestra**: Orchestration & data ingestion.  
- **dbt (Data Build Tool)**: SQL transformations & data modeling.  
- **Google BigQuery**: Cloud data warehouse.  

---

### **🎯 Goals**
✅ **Automate data ingestion & transformation**  
✅ **Maintain fresh & reliable data in BigQuery**  
✅ **Use dbt for transformation scheduling & CI/CD**  
✅ **Ensure scalable & efficient ETL workflows**  
