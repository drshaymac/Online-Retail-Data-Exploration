# Online Retail Sales Analysis
### A Mini Data Analytics Portfolio Project

---

## Project Overview

This project analyzes transactional e-commerce data from a UK-based online retailer to answer a core business question:

> **Which products are our bestsellers, and when do customers buy most?**

The dataset is sourced from [Kaggle – Online Retail Data](https://www.kaggle.com/datasets/lakshmi25npathi/online-retail-dataset) and contains 500K+ rows of invoice-level sales records. This project was completed as a structured practice exercise to build real-world data analytics skills — covering data quality assessment, cleaning, multi-dimensional analysis, visualization, and business recommendations.

---

## Dataset

| Field | Description |
|---|---|
| `InvoiceNo` | Unique invoice number (prefix `C` = cancellation/return) |
| `StockCode` | Product code |
| `Description` | Product name |
| `Quantity` | Units per transaction |
| `UnitPrice` | Price per unit (GBP) |
| `InvoiceDate` | Date and time of transaction |
| `CustomerID` | Unique customer identifier (nullable = guest checkout) |
| `Country` | Customer's country |

**Source:** UCI Machine Learning Repository via Kaggle  
**Scope after filtering:** ~46,000 rows (UK excluded, returns retained)

---

## Tools Used

- **Python** (pandas, matplotlib / seaborn)  

---

## 🔍 Phase 1: Data Quality Assessment

Before any cleaning, the raw dataset was audited for common issues:

| Check | Finding |
|---|---|
| Negative quantities | Present — indicate returns/cancellations |
| Null `CustomerID` values | Present — represent guest checkouts |
| Cancelled invoices | Flagged by `InvoiceNo` starting with `'C'` |
| Data types | `InvoiceDate` required parsing; numeric fields validated |

**Decision:** Messy data was noted and documented rather than silently dropped. 
---

## Phase 2: Data Cleaning

**Steps taken:**

1. **Excluded United Kingdom** — removes the majority of records, reducing the dataset from 500K+ to ~46K rows of international transactions
2. **Removed returns/cancellations** — rows with negative quantities and `InvoiceNo` beginning with `'C'` were removed and noted as a data quality consideration
3. **Created calculated field:**

```
TotalSales = Quantity × UnitPrice
```

**Result:** A working dataset of ~46,000 rows of non-UK transactions, with returns removed and per-line revenue calculated.

---

## Phase 3: Analysis

### Analysis 1 — Top 10 Bestselling Products (by Quantity)

Grouped by `Description`, summed `Quantity`, sorted descending.

> Identifies the highest-volume products.

---

### Analysis 2 — Top 10 Revenue-Generating Products

Grouped by `Description`, summed `TotalSales`, sorted descending.

> Volume ≠ revenue. This reveals which products actually drive the most income — not always the same list.

---

### Analysis 3 — Sales by Hour of Day

Extracted the hour from `InvoiceDate`, grouped and summed `TotalSales`.

> Reveals within the day shopping patterns critical for scheduling marketing, promotions, and staffing.

---

### Analysis 4 — Sales by Day of Week

Extracted the day of week from `InvoiceDate`, grouped and summed `TotalSales`.

> Shows weekly sales rhythm, useful for planning flash sales and email campaigns.

---

## Phase 4: Visualization

**Chart: Sales by Hour of Day (Bar Chart)**

A bar chart displaying total revenue grouped by hour shows a clear concentration of purchasing activity during **9am to 3pm**.

*A clean, labeled chart was generated with matplotlib/seaborn and exported for inclusion in the portfolio.*

---

## Phase 5: Insights & Recommendations

### Key Insight
Peak shopping activity occurs between **9 am and 3 pm**, with the highest revenue occurring at **10 am**. Approximately 70% of total sales occur within the 10 am – 3 pm window. The highest daily sales-generating window falls between Tuesday  and Thursday, with Thursday being the peak day of sales.

### Recommendation
> Schedule promotional emails and push notifications to arrive between **10 am–12 pm** to intercept customers in the lead-up to peak purchasing hours. Avoid evening campaigns — engagement drops sharply after 3 pm for this retail segment.

### Secondary Insight
The top-selling products by quantity differ meaningfully from top revenue products, suggesting a **two-tier pricing strategy** exists in the catalog — high-volume/low-margin items coexist with lower-volume/high-value items.

### Recommendation
> Maintain separate inventory and promotional strategies for each tier. Bundle high-volume items to increase basket size; spotlight high-value items in targeted campaigns to protect margin.

---

## Skills Demonstrated

- Data quality assessment and documentation
- Data cleaning and transformation
- Feature engineering (calculated fields, datetime extraction)
- Aggregation and group-by analysis
- Data visualization
- Translating data findings into actionable business recommendations

---

## What's Next (Stretch Goals)

The same dataset can answer many more business questions:

- **Repeat customer analysis** — What % of revenue comes from returning buyers?
- **Average order value by day/hour** — Does AOV vary with time?
- **Market basket analysis** — Which products are frequently bought together?
- **Customer segmentation** — RFM (Recency, Frequency, Monetary) scoring

---

## Project Structure

```
online-retail-analysis/
│
├── data/
│   └── online_retail.csv              # Raw dataset (download from Kaggle)
│
├── notebooks/
│   └── online_retail_analysis.ipynb   # Full analysis notebook
│
├── outputs/
│   ├── top10_products_quantity.csv
│   ├── top10_products_revenue.csv
│   ├── sales_by_hour.png
│   └── sales_by_day.png
│
└── README.md
```

---

## Notes

- This project was completed as a structured portfolio-building exercise inspired by a LinkedIn learning prompt.
- The focus was on **process and insight**, not on complex techniques or fancy visuals — mirroring real-world data analytics priorities.
- The dataset was filtered by **excluding** the UK for storage purposes, which reduced the dataset from 500K+ to ~46K rows.
- Returns and cancellations were **removed** from the dataset.

---

*Dataset: [Online Retail | Kaggle](https://www.kaggle.com/datasets/lakshmi25npathi/online-retail-dataset) — UCI Machine Learning Repository*
