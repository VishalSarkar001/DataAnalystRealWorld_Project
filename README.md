Retail Loyalty Analytics 

Data Quality, Loyalty Points & RFM Segmentation
Project Overview
This project implements a Retail Loyalty Analytics system.
The objective is to build an end-to-end data engineering pipeline that:
Ingests retail datasets from CSV files
Applies data quality rules to segregate clean and bad data
Calculates loyalty points for customers
Performs RFM (Recency, Frequency, Monetary) analysis
Identifies High-Spenders and At-Risk customers
The entire pipeline is implemented using Python (Pandas) in Google Colab.

Objectives
✔ Ingest retail data from CSV files
✔ Apply data quality validations
✔ Segregate clean and rejected records
✔ Calculate loyalty points using business rules
✔ Update customer loyalty balances
✔ Perform RFM analysis
✔ Segment customers into High-Spenders and At-Risk

Dataset	                     Description
stores.csv	                 Store master data
products.csv	               Product catalog
customer_details.csv	       Customer master data
store_sales_header.csv	     Transaction-level sales data
store_sales_line_items.csv	 Line-item level sales data
loyalty_rules.csv	           Loyalty points configuration

Phase 1: Data Ingestion & Quality Validation
Data Quality Rules Applied
NULL / missing mandatory fields
Negative or invalid numeric values
Invalid email and phone formats
Future or invalid dates
Referential integrity violations
Duplicate business keys
Output:
For each dataset:
clean_<dataset>.csv → Valid records
rejected_<dataset>.csv → Invalid records with reject_reason
This ensures only clean data flows downstream.

Phase 2: Loyalty Point Calculation
Business Logic
For each transaction:
If total_amount ≥ min_spend_threshold:
    earned_points = (total_amount × points_per_unit_spend) + bonus_points
Else:
    earned_points = 0
Steps
Calculate loyalty points at transaction level
Aggregate earned points at customer level
Update total_loyalty_points for each customer
Output
customers_with_updated_loyalty_points.csv

RFM Metrics
Recency (R) → Days since last purchase
Frequency (F) → Number of transactions
Monetary (M) → Total spend
RFM Scoring
Quartile-based scoring (1–4)
Combined RFM Score

Customer Segmentation
Segments Defined 
High-Spenders
Top 10% customers by monetary value
At-Risk
No purchase in last 30+ days
Still have loyalty points
Output
customer_rfm_segmentation.csv












