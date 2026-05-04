# 🛒 Online Retail — Data Cleaning & EDA

A complete data cleaning and exploratory data analysis project built on a real-world e-commerce dataset. The goal was to take a messy, raw transactional dataset and turn it into something clean, reliable, and ready for analysis — then pull out useful insights through visualizations.

---

## 📁 Dataset

**Source:** [Online Retail Dataset — Kaggle](https://www.kaggle.com/datasets/ulrikthygepedersen/online-retail-dataset)

The dataset contains ~541,000 rows of transactional records from a UK-based online retail store, covering 2010–2011. Each row represents one product purchased as part of an invoice.

**Columns:** `InvoiceNo`, `StockCode`, `Description`, `Quantity`, `InvoiceDate`, `UnitPrice`, `CustomerID`, `Country`

---

## 🧹 Data Cleaning Steps

The raw data had several real-world issues that needed fixing before any analysis could be done:

- **Null values** — Dropped rows where `CustomerID` or `Description` was missing (~135K rows affected)
- **Duplicate rows** — Identified and removed using `drop_duplicates()`
- **Cancelled orders** — Filtered out invoices starting with `"C"`, which represent returns/reversals
- **Negative quantities & prices** — Removed rows where `Quantity <= 0` or `UnitPrice <= 0`
- **Data type fix** — Converted `InvoiceDate` from string to datetime format
- **Feature engineering** — Created `Total_Price` (Quantity × UnitPrice), extracted `Month` and `Year`
- **Column standardization** — Renamed all columns to lowercase

After cleaning: **~397,884 rows** remained from the original 541,909.

---

## 📊 Visualizations

### 1. Top 10 Countries by Revenue
A bar chart comparing total sales across countries. The UK leads by a huge margin, followed by Netherlands, Ireland, Germany, and France.

### 2. Order Value Distribution
A histogram showing how individual order values are spread. Most orders are under £50, with the distribution heavily right-skewed — typical of a retail store serving both everyday buyers and occasional bulk purchasers.

### 3. Monthly Sales Trend
A line chart tracking total revenue month by month. Sales stay relatively flat through early 2011 and then spike sharply in October–November — a clear signal of holiday season demand.

### 4. Correlation Heatmap
Shows the relationships between `Quantity`, `UnitPrice`, and `Total_Price`. Quantity and Total Price are strongly correlated (as expected), while Unit Price has a weaker relationship with the others.

---

## 💡 Key Insights

- The **UK dominates revenue**, contributing the vast majority of total sales
- Most customers make **small purchases under £50** — bulk buyers are the exception
- Sales peak sharply in **November**, pointing to strong pre-Christmas shopping behaviour
- About **25% of records** were removed during cleaning due to cancellations, missing data, or invalid entries

---

## 🛠️ Tools & Libraries

| Tool | Purpose |
|------|---------|
| Python | Core language |
| Pandas | Data loading, cleaning, manipulation |
| Matplotlib | Plotting charts |
| Seaborn | Statistical visualizations |
| Jupyter Notebook | Development environment |
