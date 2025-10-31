# NYC Taxi Data Analysis with PySpark on Databricks

This repository contains a PySpark notebook for analyzing NYC Yellow Taxi trip data on Databricks. The project performs data merging, cleaning, analysis, and exports results to Azure SQL Database.

## 📋 Overview

This project processes 21 months of NYC Yellow Taxi trip data (January 2024 - September 2025) and generates analytical insights including:
- Top 10 pickup zones by month
- Average trip duration trends
- Distance analysis by payment type
- Fare analysis by passenger count
- Monthly tip totals

## 🗂️ Project Structure

```
Taxi_databricks/
├── Sparkexercice.ipynb    # Main PySpark notebook
├── README.md              # This file
└── LICENSE                # Project license
```

## 🚀 Features

### 1. Data Merging
- Loads 21 monthly tables of Yellow Taxi trip data
- Handles schema differences across months
- Adds missing columns with null values
- Unions all datasets into a single raw table

### 2. Data Cleaning
- Identifies and removes duplicate records
- Creates a clean dataset for analysis

### 3. Analytical Queries
Creates the following analytical tables:

- **`Top_10_pickup_zones`**: Identifies the 10 most frequent pickup locations each month
- **`avg_trip_duration_per_month`**: Calculates average trip duration by month (in seconds)
- **`avg_distance_by_payment_type`**: Determines average distance traveled by payment method
- **`avg_amount_by_passenger_count`**: Estimates average fare amount by number of passengers
- **`total_tip_per_month`**: Measures total tips collected each month

### 4. Data Export
- Exports all analytical tables to Azure SQL Database
- Uses JDBC connection for secure data transfer
- Tables prefixed with `lr_` in the target database

## 🛠️ Prerequisites

- Databricks workspace
- Access to NYC Yellow Taxi trip data tables
- Azure SQL Database (for export)
- Required libraries:
  - PySpark
  - Microsoft SQL Server JDBC Driver

## 📊 Data Sources

The notebook expects the following tables in the `default` database:
- `yellow_tripdata_2024_01` through `yellow_tripdata_2024_12`
- `yellow_tripdata_2025_01` through `yellow_tripdata_2025_09`

## 🔐 Environment Variables

The following environment variables are required for database export:
- `LOGIN`: Azure SQL Database username
- `PASS`: Azure SQL Database password

## 🎯 Usage

1. Upload the notebook to your Databricks workspace
2. Ensure source tables are available in the `default` database
3. Set required environment variables for SQL export
4. Run all cells sequentially

## 📈 Output Tables

All output tables are saved in the `default` database:
- `Raw_table`: Merged raw data
- `clean_table`: Deduplicated data
- `Top_10_pickup_zones`
- `avg_trip_duration_per_month`
- `avg_distance_by_payment_type`
- `avg_amount_by_passenger_count`
- `total_tip_per_month`

## 📝 Notes

- The notebook uses schema merging to handle column differences
- All monetary values are rounded to 2 decimal places
- Trip duration is calculated in seconds
- Data is exported with `overwrite` mode

## 📄 License

See LICENSE file for details.