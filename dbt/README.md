# NY Taxi Data Transformation with dbt  

## 📌 Overview  
This project implements a **data transformation pipeline** using **dbt (Data Build Tool)** to process and analyze New York City taxi trip data. It follows the **best practices of analytics engineering** to clean, transform, and structure the data for reporting and insights. The project is part of the **Data Engineering Zoomcamp**.  

## 🏗️ Project Structure  

```
NY_Taxi_DBT/
├── macros/                      # Custom SQL macros for transformations
│   ├── get_payment_type.sql
├── models/
│   ├── staging/                 # Staging models (raw data processing)
│   │   ├── stg_green_tripdata.sql
│   │   ├── stg_yellow_tripdata.sql
│   │   └── schema.yml           # Schema definitions & tests for staging models
│   ├── marts/                   # Data marts (final reporting tables)
│   │   ├── fact_trips.sql       # Fact table with trip details
│   │   ├── dim_zones.sql        # Dimension table for taxi zones
│   │   ├── dm_monthly_revenue.sql # Monthly revenue summary
│   │   └── schema.yml           # Schema definitions & tests for marts
├── seeds/                       # Preloaded reference data
│   ├── taxi_zone_lookup.csv     # Seed file for taxi zones
├── dbt_project.yml              # dbt project config  
├── packages.yml                 # dbt package dependencies  
└── README.md                    # Project documentation  
```

## 📊 Data Sources  
The dataset contains NYC taxi trip records, including:  
- **Green Taxi Trips** (`green_tripdata`)  
- **Yellow Taxi Trips** (`yellow_tripdata`)  
- **Taxi Zones Metadata** (`taxi_zones`)  

## 🔄 dbt Transformations  

This project follows a structured **dbt modeling approach**:  

1. **Staging Models (`stg_*`)**  
   - Clean & rename columns  
   - Convert data types  
   - Standardize timestamps  

2. **Intermediate Models**  
   - Join datasets  
   - Apply transformations & aggregations  

3. **Final Models (Data Marts)**  
   - **`fact_trips.sql`** → Central fact table with taxi trip details  
   - **`dim_zones.sql`** → Lookup table for taxi zones  
   - **`dm_monthly_revenue.sql`** → Aggregated monthly revenue data  

## 🛠️ Macros  

The **`macros/`** folder contains **custom SQL functions** to simplify transformations:  
- **`get_payment_type.sql`** →  This macro returns the description of the payment_type  

## 📌 Seeds  

The **`seeds/`** folder contains **static reference data** used in transformations:  
- **`taxi_zone_lookup.csv`** Taxi Zones roughly based on NYC Department of City Planning's Neighborhood
      Tabulation Areas (NTAs) and are meant to approximate neighborhoods, so you can see which
      neighborhood a passenger was picked up in, and which neighborhood they were dropped off in. 
      Includes associated service_zone (EWR, Boro Zone, Yellow Zone)
  
## 🎯 Features  

✅ **Automated data transformations** using dbt  
✅ **Staging & data marts structure** for efficient analytics  
✅ **Schema validation & data testing** for data quality  
✅ **Seed data for static reference tables**  
✅ **Reusable SQL macros** for modular transformations  
✅ **BigQuery integration** for scalable cloud-based analytics  
✅ **Scheduled dbt Jobs** to **refresh data daily**  
✅ **CI/CD Pipeline** for automated dbt runs & testing  


