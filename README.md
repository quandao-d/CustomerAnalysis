# CustomerAnalysis
This project performs clustering analysis on sales transaction data using R. The goal is to segment customer behavior, analyze product performance, and explore sales trends.

---

## 📁 Dataset Overview

- **Source**: IEBS Masterclass
- **Rows**: 4.805 transactions
- **Columns**: 7 features including orderID, clientID, product, gender, orderdate, Quantity,Price

---

## Analysis Plan

### 1. Product Analysis
- Identify product categories
- Determine best-selling and underperforming products
- Evaluate product preferences by gender

### 2. Sales Analysis
- Track monthly sales trends
- Evaluate performance by time of day and day of week
- Understand pricing and quantity patterns

### 3. Customer Analysis
- Segment customers using clustering
- Analyze customer types and payment methods
- Examine behavior by gender, time, and frequency

---

## Methodology

### Data Cleaning
- Converted `orderdate` to `Date` format
- Removed unnecessary columns: `clientId`, `orderId`, `orderdate`, etc.
- Encoded categorical variables:
  - `gender`: male → 1, female → 0
  - `product`: factorized numerically
- Handled missing values with `na.omit()`

### Feature Engineering
- Created new columns:
  - `month`: to aggregate monthly trends
  - `product`: numeric factor for clustering
- Removed non-numeric fields for modeling

### Clustering (K-Means)
- Scaled data with `scale()`
- Determined optimal clusters using:
  - Elbow Method (`wss`)
  - Silhouette Method
  - Gap Statistic
- Chose **k = 3**
- Assigned cluster labels to each transaction

---

## 📊 Exploratory Data Analysis (EDA)

- **Product frequency barplot**
- **Monthly sales frequency**
- **Gender-product heatmap**
- **Cluster visualizations (colored by label)**

---

## Cluster Summary

Each cluster is analyzed by:

- **Gender distribution**
- **Product preferences**
- **Average quantity and price**
- **Sales volume**

> Summary tables and plots are printed per cluster.

---

## Business Questions Answered

| Question | Answered in Script |
|---------|--------------------|
| Which product sells most? | ✅ |
| Who buys more — by gender, type? | ✅ |
| When do customers spend more? | ✅ |
| Cluster-based segmentation? | ✅ |

---

## Files

| File | Description |
|------|-------------|
| `Transactions (1).csv` | Raw dataset |
| `clusteranalysis.R` | Main R script |
| `README.md` | Project overview |

---

## 📚 Libraries Used

- `ggplot2`
- `reshape2`
- `dplyr`
- `factoextra`
- `cluster`
