📦 Online Retail Analysis

This project presents a complete ETL and Data Analysis pipeline for an online retail transaction dataset. The goal is to understand customer behavior, product popularity, and sales trends to generate insights that can inform better business strategies for marketing, inventory management, and pricing optimization.

📂 Dataset Content
The dataset is sourced from Kaggle and contains historical transaction data from a UK-based online retail store.

Key columns:

InvoiceNo: Unique transaction code

StockCode: Product identifier

Description: Product name

Quantity: Number of units sold

InvoiceDate: Date of transaction

UnitPrice: Price per unit

CustomerID: Identifier for each customer

Country: Customer location

💼 Business Requirements

Understand customer engagement and segmentation.

Identify top-selling products to optimize inventory and marketing.

Analyze sales patterns over time to support forecasting.

❓ Hypotheses and How to Validate

Hypothesis Validation Approach
High-spending customers shop more frequently Use RFM analysis (Recency, Frequency, Monetary)
Certain products consistently sell more Group by ProductName and rank by total quantity
Sales show monthly seasonality Aggregate sales by Month and plot trends

🗺️ Project Plan

ETL Pipeline

Import libraries

Data extraction & cleaning

Feature engineering

Customer Behavior Analysis

RFM metrics

Top spender analysis

Product Analysis

Popular product identification

Top 10 products visualization

Sales Trend Analysis

Time-based sales aggregation

Visual trend detection

🔗 Mapping Business Requirements to Visualizations

Requirement Visualization
Identify loyal customers Bar chart of top 10 customers by spending
Spot high-demand products Seaborn bar chart of top-selling products
Detect seasonality Line chart (monthly/daily sales) using Matplotlib & Plotly

📊 Analysis Techniques Used

RFM Analysis (Recency, Frequency, Monetary)

Descriptive Statistics (Total sales, avg. transaction value)

Grouping & Aggregation (e.g., by month, customer, product)

Data Visualizations using:

Matplotlib for static charts

Seaborn for polished visuals

Plotly for interactive charts

⚠️ Data Type & Import Handling

Issue 1: InvoiceDate Becomes object When Reloaded
During the ETL process, InvoiceDate was correctly converted to datetime.

However, when saved to CSV and reloaded in another notebook, it appeared as object (string).

This occurred because CSV files store dates as plain text.

✅ Solution

Use the parse_dates parameter when reading the CSV:

df = pd.read_csv('cleaned_data.csv', parse_dates=['InvoiceDate'])
Issue 2: DtypeWarning Due to Mixed Types in InvoiceNo
Warning:

DtypeWarning: Columns (0) have mixed types. Specify dtype option on import or set low_memory=False.
The InvoiceNo column contains mixed types (likely due to string prefixes like 'C' for cancellations).

✅ Solution
Convert InvoiceNo to numeric:

df['Invoice'] = pd.to_numeric(df['Invoice'], errors='coerce').astype('Int64')
Ensure InvoiceDate is also properly parsed:

df['InvoiceDate'] = pd.to_datetime(df['InvoiceDate'])

Known Issue: Country and Weekday Columns
Attempts to convert Country and Weekday to the string dtype were unsuccessful due to pandas/environment constraints.

These columns currently remain as object dtype and may be updated in future releases for optimized string handling.

⚖️ Ethical Considerations

Data Integrity: Only valid transactions (non-cancelled, non-zero quantities) are included.

🐞 Unfixed Bugs

Hover info in Plotly charts occasionally overlaps on smaller screens.

Product naming inconsistencies may still exist due to free-text entries.

Country and Weekday columns remain in object dtype.

🚧 Development Roadmap

Build ETL pipeline

Conduct RFM analysis

Explore sales trends

Deploy dashboard (e.g., Tableau)

Automate ETL workflow with scheduling (e.g., Airflow)

Convert object columns (Country, Weekday) to pandas string dtype when environment supports it

Implement interactive visualization to identify high-value, low-frequency customers using Plotly or similar tool

🧰 Main Data Analysis Libraries

Pandas – Data manipulation

NumPy – Numerical operations

Matplotlib – Static visualizations

Seaborn – Enhanced charts

Plotly – Interactive plotting

👩‍💻 Credits
Project by: Angelnesakumari Jayakumar
Email: angeljayakumar86@gmail.com
Location: Mitcham, United Kingdom

📑 Content
etl_pipeline.py – Scripts for data loading and cleaning

customer_analysis.py – Customer behavior analysis

product_analysis.py – Product trend analysis

sales_trend.py – Time-based sales trend analysis

visuals/ – All generated visualizations

🙏 Acknowledgements
Kaggle for dataset access

Open-source Python libraries

Bootcamp mentors for guidance

Family for continuous support during this journey
