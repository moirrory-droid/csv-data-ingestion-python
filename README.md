# csv-data-ingestion-python
Python data ingestion and validation mini-project using pandas. Loads raw CSV data, performs data profiling, checks for missing values and duplicates, handles UK date parsing, and engineers time-based features. Demonstrates foundational data engineering concepts including schema validation and preprocessing.

Project Overview

This is my first Python-based data engineering mini project.
After completing a SQL sales analysis project using the Superstore dataset, I wanted to begin learning Python and understand how raw data is ingested, validated, and prepared before reaching a database or BI tool.

This project focuses on:

Loading raw CSV data
Performing data profiling
Validating data quality
Handling date parsing issues
Engineering basic time-based features
This marks the beginning of my Python journey.

Objective

To simulate the first stage of a data engineering pipeline:
Raw CSV → Validation → Cleaning → Structured Data
Rather than focusing on advanced Python, this project focuses on understanding:
How data enters a system
How schema validation works
Where pipelines commonly break (e.g., date parsing)
How to prevent silent data issues

Tools Used

Python 3
pandas
VS Code
Git / GitHub

Dataset

Superstore sales dataset (same dataset used in my SQL project).
Includes:
Order information
Customer information
Product categories
Sales values
Order and Ship dates

Steps Performed

1️. Load Raw CSV
Used pandas to ingest the dataset into a DataFrame.

<img width="2048" height="1190" alt="image" src="https://github.com/user-attachments/assets/8b0a67b6-860d-41c5-bb89-6e668b54b153" />

VS Code view of pd.read_csv() code
First 5 rows output (df.head())

2️. Data Profiling

Inspected:
First rows (df.head())
Column names
Data types
Summary statistics

Terminal output showing 
.head()
.dtypes
.describe()

This step helped understand the schema and data structure before transformation.

3️. Data Quality Validation

Checked for:
Missing values
Duplicate rows

df.isnull().sum()
df.duplicated().sum()

Result:
No missing values
No duplicate rows

<img width="2048" height="1190" alt="image" src="https://github.com/user-attachments/assets/e94af4eb-94d4-419b-b2e0-aed63374b062" />

Terminal output showing 0 missing + 0 duplicates.
This reflects a common first step in data engineering pipelines.

4️. Date Parsing Issue (Key Learning Moment)

Initial attempt to convert dates failed due to UK date format (DD/MM/YYYY).
Error example:

ValueError: time data '15/04/2018' doesn't match format '%m/%d/%y'

This highlighted a real-world issue:
Different regions store dates differently.

Fix implemented:

pd.to_datetime(..., dayfirst=True, errors="coerce")

Validation:
Confirmed 0 failed conversions
Confirmed correct datetime types

<img width="2048" height="1190" alt="image" src="https://github.com/user-attachments/assets/4247aa6b-acb9-430a-8310-e82705ccb957" />
<img width="2048" height="1190" alt="image" src="https://github.com/user-attachments/assets/258fd3c3-2253-4d20-bf63-4b244b529758" />


The error message
The corrected output showing datetime64 types
This was a valuable lesson in defensive data engineering.

5️. Feature Engineering

Created new structured time columns:

order_year
order_month
order_dayofweek

This mirrors how data is prepared before loading into warehouses or dashboards.

<img width="1552" height="902" alt="Screenshot 2026-02-21 at 05 28 18" src="https://github.com/user-attachments/assets/54605795-a48e-44dd-8fdd-1ae8a5d52143" />

Output showing new columns

Key Learning Points

Always validate schema before transformation
Date parsing is a common pipeline failure point
Never assume regional formatting
Use defensive coding practices (errors="coerce")
Data ingestion is a critical stage before analytics

Connection to My SQL Project

This Python project complements my SQL repository:
SQL project focuses on analytical querying
This project focuses on ingestion and validation
Together they represent:

Data ingestion → Data structuring → Data analysis
