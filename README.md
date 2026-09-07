adding MA50 , MA200 on 22-07-2026
01-09-2026
mergerd gold and silver etf  
create a python code to fetch historcal data from yahoo finance and then join in main file

---------------------
# Live Market Data Pipeline

 ## Project Overview

 A scheduled data engineering pipeline built with Python, PySpark, Databricks, and Delta Lake to automatically collect financial market data from Yahoo Finance and store it for historical analysis.

 ## Project Milestone — 07 September 2026

 On 07-09-2026, I migrated my market-data collection process from my local Python environment to a Databricks scheduled Job.

 Previously, the Python script had to run continuously on my local computer. This meant the data collection stopped whenever my local system was turned off.

 The new Databricks implementation runs independently in the cloud, so I no longer need to keep my local computer running.

 <img width="1368" height="834" alt="image" src="https://github.com/user-attachments/assets/1e5ddaa0-6454-47c0-b584-328dd140f61b" />

 ## Architecture

```
Yahoo Finance
      ↓
Python / urllib
      ↓
Databricks Notebook
      ↓
PySpark
      ↓
Delta Table
      ↓
Databricks Scheduled Job
      ↓
Automatic execution every 5 minutes
```

 ## Data Collected

 The pipeline currently collects:

 - Silver futures (SI=F)
- Gold futures (GC=F)
- USD/INR exchange rate
- NSE index
- BSE Sensex
- Gold ETF (GOLDBEES.NS)
- Silver ETF (SILVERBEES.NS)

 It also calculates estimated INR prices for gold and silver per gram and kilogram.

 ## Technologies

 - Python
- PySpark
- Apache Spark
- Databricks
- Delta Lake
- SQL
- Yahoo Finance API
- Pandas
- Azure / Cloud Data Engineering concepts

 ## Scheduling

 The Databricks Job is configured as:

```
Trigger: Scheduled
Schedule: Interval
Frequency: Every 5 minutes
Status: Active
Compute: Serverless Autoscaling
```

 Each execution:

 1. Fetches the latest market data.
2. Processes the data using Python.
3. Creates a Spark DataFrame.
4. Appends one record to the Delta table.
5. Finishes the Job.

 The next scheduled execution then repeats the process.

 ## Delta Table

 The collected data is stored in:

```
1_live_market_catalog
└── 2_live_market_schema
    └── live_market
```

 The table contains timestamp, date, market prices, calculated INR values, equity indices, and ETF prices.

 ## Why I Built This

 This project was created as a practical Data Engineering project to understand and demonstrate:

 - Data ingestion
- API-based data collection
- Python data processing
- PySpark DataFrames
- Delta Lake
- Databricks Jobs
- Scheduled pipeline execution
- Cloud-based data collection
- Historical data storage
- Basic data engineering reliability

 ## Local vs Databricks

 ### Earlier — Local Python

```
Local Computer
      ↓
Python Script
      ↓
Yahoo Finance
      ↓
Data Storage
```

 The computer had to remain switched on for continuous collection.

 ### Now — Databricks

```
Databricks
      ↓
Scheduled Job
      ↓
Python / PySpark
      ↓
Yahoo Finance
      ↓
Delta Table
```

 The collection process is now independent of my local computer.

 ## Future Improvements

 Planned improvements include:

 - Data quality validation
- Better API retry handling
- Market-hours scheduling
- Additional financial instruments
- Data visualization with Power BI
- Historical trend analysis
- Pipeline monitoring and alerting
- Automated data-quality checks
- Partitioning and optimization of the Delta table

 ## Project Status

 Active — Data Collection in Progress

 The pipeline is currently scheduled to collect market data every 5 minutes and build a historical dataset for future analysis.

 ## Milestone

 07 September 2026 — First successful Databricks scheduled pipeline

 The pipeline successfully moved from a locally executed Python process to a cloud-scheduled Databricks Job.
