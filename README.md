# 📦 Online Retail Analysis

This project is a basic, beginner-friendly data analytics project that presents a ETL (Extract, Transform, Load) and data analysis pipeline using an online retail transaction dataset. Designed to be accessible for those new to data analysis, it explores customer behavior, product popularity, and sales trends to generate simple yet meaningful insights for improving marketing, inventory management, and pricing strategies.

![My Image](data/images/online_shopping.png)

## 📂 Dataset Content

The dataset is sourced from Kaggle and contains historical transaction data from a UK-based online retail store.

### Key columns:

InvoiceNo: Unique transaction code

StockCode: Product identifier

Description: Product name

Quantity: Number of units sold

InvoiceDate: Date of transaction

UnitPrice: Price per unit

CustomerID: Identifier for each customer

Country: Customer location

## 💼 Business Requirements

Understand customer engagement and segmentation.

Identify top-selling products to optimize inventory and marketing.

Analyze sales patterns over time to support forecasting.

## ❓ Hypotheses and How to Validate

Hypothesis Validation Approach

High-spending customers shop more frequently Use RFM analysis (Recency, Frequency, Monetary)

Certain products consistently sell more Group by ProductName and rank by total quantity

Sales show monthly seasonality Aggregate sales by Month and plot trends

## 🗺️ Project Plan

### ETL Pipeline

Import libraries

Data extraction & cleaning

Feature engineering

### Customer Behavior Analysis

RFM metrics

Top spender analysis

### Product Analysis

Popular product identification

Top 10 products visualization

### Sales Trend Analysis

Time-based sales aggregation

## Mapping Business Requirements to Visualizations

Requirement Visualization

Identify loyal customers Bar chart of top 10 customers by spending

Spot high-demand products Seaborn bar chart of top-selling products

Detect seasonality Line chart (monthly/daily sales) using Matplotlib & Plotly

## 📊 Analysis Techniques Used

RFM Analysis (Recency, Frequency, Monetary)

Descriptive Statistics (Total sales, avg. transaction value)

Grouping & Aggregation (e.g., by month, customer, product)

## Data Visualizations using:

Matplotlib for static charts

Seaborn for polished visuals

Plotly for interactive charts

## Fixed Issues

### Issue 1: InvoiceDate Becomes object When Reloaded

    ⚠️ Data Type & Import Handling

During the ETL process, InvoiceDate was correctly converted to datetime.

However, when saved to CSV and reloaded in another notebook, it appeared as object (string).

This occurred because CSV files store dates as plain text.

✅ Solution

Use the parse_dates parameter when reading the CSV:

df = pd.read_csv('cleaned_data.csv', parse_dates=['InvoiceDate'])

### Issue 2: DtypeWarning Due to Mixed Types in InvoiceNo

Warning:

DtypeWarning: Columns (0) have mixed types. Specify dtype option on import or set low_memory=False.
The InvoiceNo column contains mixed types (likely due to string prefixes like 'C' for cancellations).

✅ Solution
Convert InvoiceNo to numeric:

df['Invoice'] = pd.to_numeric(df['Invoice'], errors='coerce').astype('Int64')
Ensure InvoiceDate is also properly parsed:

df['InvoiceDate'] = pd.to_datetime(df['InvoiceDate'])

## ⚖️ Ethical Considerations

Data Integrity: Only valid transactions (non-cancelled, non-zero quantities) are included.

## 🐞 Unfixed Bugs

Hover info in Plotly charts occasionally overlaps on smaller screens.

Product naming inconsistencies may still exist due to free-text entries.

Country and Weekday columns remain in object dtype.

Attempts to convert Country and Weekday to the string dtype were unsuccessful due to pandas/environment constraints.

These columns currently remain as object dtype and may be updated in future releases for optimized string handling.

## 🚧 Development Roadmap

Build ETL pipeline

Conduct RFM analysis

Explore sales trends

Deploy dashboard (e.g., Tableau)

Automate ETL workflow with scheduling (e.g., Airflow)

Convert object columns (Country, Weekday) to pandas string dtype when environment supports it

Implement interactive visualization to identify high-value, low-frequency customers using Plotly or similar tool

## 🧰 Main Data Analysis Libraries

Pandas – Data manipulation

NumPy – Numerical operations

Matplotlib – Static visualizations

Seaborn – Enhanced charts

Plotly – Interactive plotting

## 📑 Content

etl_pipeline.py – Scripts for data loading and cleaning

customer_analysis.py – Customer behavior analysis

product_analysis.py – Product trend analysis

sales_trend.py – Time-based sales trend analysis

## 👩‍💻 Credits

### Contributors

Angelnesakumari Jayakumar - Data Manager, Data Analyst, and Project Manager

### Libraries and Tools

- Pandas - Used for data manipulation and analysis (License: BSD-3-Clause)

- Matplotlib - Used for data visualization and plotting (License: PSF)

- Jupyter Notebook - Used for interactive data analysis (License: BSD-3-Clause)

- Visual Studio Code - Used as the primary code editor and development environment (License: MIT)

- Python Tutor - Used for visualizing and understanding Python code execution (License: MIT)

- Grok - AI assistant for project guidance and troubleshooting, created by xAI

- ChatGPT - AI assistant for additional project support, created by OpenAI

### Asset

Alamy - Provided the image used in the README (Photographer: Eric Muhamad Naris ,https://www.alamy.com/cartoon-flat-style-drawing-active-man-coming-out-of-monitor-computer-screen-with-holding-shopping-bags-sale-digital-lifestyle-consumerism-online-s-image558945272.html]

## 🙏 Acknowledgements

This project is a significant milestone, marking my return to coding as a stay-at-home mum after university. As a basic beginner-friendly project, it’s designed to be accessible to others learning data analysis. A huge thank you to everyone who supported me in bringing this project to life:

- Mark Briscoe - For teaching Python coding and guiding us through setting up Visual Studio Code.

- John Rearden - For his insightful lessons on managing virtual environments in Visual Studio Code.

- Niall Maher - For teaching data analytics topics, including data visualization.

- Emma Lamont - For her invaluable guidance and detailed insights during daily stand-ups and stand-downs.

- YouTube Community - For countless tutorials and walkthroughs that helped clarify few concepts.

- My bootcamp peers - For their feedback and collaboration throughout the project.

- My wonderful husband - For his endless patience, encouragement, and support during study sessions.

- My amazing little kids - For their smiles and love that kept me motivated every step of the way.
