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

### Issue: `InvoiceDate` Becomes `object` When Reloaded

- During the ETL process, `InvoiceDate` was correctly converted to `datetime`.
- However, when saved to CSV and reloaded in another notebook, it appeared as `object` (string).
- This happened because CSV files store dates as plain text.

### ✅ Solution

Use the `parse_dates` parameter when reading the CSV:

```python
df = pd.read_csv('cleaned_data.csv', parse_dates=['InvoiceDate'])


## Future Work

- Customer segmentation analysis postponed due to time constraints.
- (Additional enhancements to be added here for future delivery.)


```
