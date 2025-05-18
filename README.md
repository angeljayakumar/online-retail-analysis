# 🛍️ Online Retail Customer Behaviour Analysis

This project analyzes customer behavior using a retail transaction dataset from [Kaggle](https://www.kaggle.com/datasets/abhishekrp1517/online-retail-transactions-dataset). It includes data cleaning (ETL), descriptive statistics, and RFM (Recency, Frequency, Monetary) analysis to understand purchasing patterns.

---

## 📁 Project Structure

- `etl_cleaning.ipynb`: Extract, clean, and transform the dataset.
- `customer_behaviour.ipynb`: Analyze customer behavior and segment customers.
- `sales_trends.ipynb`: Analyze sales patterns over time (planned).
- `product_trends.ipynb`: Identify top-selling products (planned).

---

## ⚠️ Date Column Handling

### Issue 1: `InvoiceDate` Becomes `object` When Reloaded

- During the ETL process, `InvoiceDate` was correctly converted to `datetime`.
- However, when saved to CSV and reloaded in another notebook, it appeared as `object` (string).
- This happened because CSV files store dates as plain text.

### ✅ Solution

Use the `parse_dates` parameter when reading the CSV:

```python
df = pd.read_csv('cleaned_data.csv', parse_dates=['InvoiceDate'])



### Issue 2: DtypeWarning Due to Mixed Types in Invoice Column

When loading the dataset with pd.read_csv, a warning appeared:


DtypeWarning: Columns (0) have mixed types. Specify dtype option on import or set low_memory=False.
This means the Invoice column (column 0) contains mixed data types, which can cause problems during analysis.

✅ Solution
Based on Kaggle data review, convert the Invoice column explicitly to numeric:

df['Invoice'] = pd.to_numeric(df['Invoice'], errors='coerce').astype('Int64')


Convert the InvoiceDate column to datetime:


df['InvoiceDate'] = pd.to_datetime(df['InvoiceDate'])
This ensures consistent types for analysis and avoids the warning.

🔧 Pending Fixes for Other Object Columns
The following columns remain as object and need review/conversion:

StockCode

ProductName

Country

Weekday

These will be addressed in future updates.



## Future Work

- Implement interactive visualization for identifying high-value, low-frequency customers using Plotly or another suitable tool to enhance insight into customer segments.



- (Additional enhancements to be added here for future delivery.)


```
