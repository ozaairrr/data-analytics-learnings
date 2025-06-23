
# 🧹 Power BI Data Cleaning & Transformation Project – Bank Transactions

## 📌 Objective

This mini-project focuses on using **Power Query in Power BI** to clean, transform, and normalize real-world financial datasets. The goal was to practice data shaping, merging, filtering, and enrichment by cleaning inconsistencies and preparing the data model for reporting and analysis.

---

## 📁 Datasets Used

- `fact_transactions_2022.csv`
- `fact_transactions_2023.csv`
- `dim_merchants.csv`
- `pivoted_dim_category.csv`
- `dim_date.csv`

---

## ✅ Tasks & Solutions

### 🔹 Task 1: Clean Merchant Data
- Used **“Use First Row as Headers”** to correct the header row.
- Extracted `Merchant` and `Industry Segment` using **“Text Before Delimiter”** (`" - "`).
- Created a custom column using **“Column From Examples”** for `Industry Segment`.
- Applied **Trim** function to remove unwanted spaces.
- Removed **duplicate merchant entries** to ensure unique merchants.

---

### 🔹 Task 2: Extract Date Parts from `dim_date`
- From the `dim_date` table, extracted:
  - `Year`
  - `Month Name`
  - `Day Name`
- Used the **“Date” → “Year”, “Month”, “Day”** features in the **Add Column** tab.

---

### 🔹 Task 3: Unpivot the `pivoted_dim_category` Table
- Selected all the store code columns and applied **“Unpivot Columns”** to normalize.
- Used **“Use First Row as Headers”** post-transformation to clean up the column names.
- Final result: Table contains `CategoryType`, `Store_ID`, and `Value`.

---

### 🔹 Task 4: Filter Transactions < ₹100
- Applied a **Number Filter** (`Debit Amount >= 100`) on both:
  - `fact_transactions_2022`
  - `fact_transactions_2023`

---

### 🔹 Task 5: Append Tables
- Used **“Append Queries as New”** to merge `fact_transactions_2022` and `fact_transactions_2023` into a new table named `fact_transactions`.

---

### 🔹 Task 6: Merge Tables for Enrichment
- Merged `fact_transactions` with:
  - `dim_merchants` (on `Merchant_ID`)
  - `dim_category` (on `Category_ID`)
- Used **Left Outer Join** and expanded required fields (`Merchant Name`, `Category Name`) directly into `fact_transactions`.

---

### 🔹 Task 7: Add Conditional Column
- Added a new column: `Transaction Category`
  - If `Debit Amount > 1000` → **High**
  - Else → **Low**
- Used **“Add Column” → “Conditional Column”**.

---

### 🔹 Task 8: Group & Sort by Merchant
- Duplicated the `fact_transactions` table.
- Applied **Group By** on the `Merchant` column.
- Aggregated the **sum of Debit Amount** as `Total_Transaction_Amount`.
- Sorted the values in **descending order** for better visibility.

---

## 📊 Tools & Skills Applied

- Power BI (Power Query)
- Data Cleaning & Filtering
- Column Extraction & Splitting
- Unpivoting & Normalization
- Merging Dimension Tables
- Conditional Columns
- Grouping & Aggregation
  
---

### 💡 Power BI Dashboard Preview

The dashboard presents a high-level view of merchant-wise debit activity, transaction volume, and trend analysis. It includes:

- Top merchants by total debit amount
- Total debit volume and transaction count
- Quarterly debit trends
- Transaction category breakdown (High vs Low)
- Interactive merchant slicer

![Bank Transactions Dashboard](https://github.com/ozaairrr/data-analytics-learnings/blob/d1f29bbd50139d38d0eb96b8bc97e15cc95c594b/power-query-data-cleaning-bank-transactions/Bank_Transactions_Dashboard.png?raw=true)

---

### 🎥 Dashboard Preview

[![Watch the Demo](https://img.youtube.com/vi/OmCB_r_nMgo/0.jpg)](https://youtu.be/OmCB_r_nMgo)

---

## 🧠 Learning Outcome

This assignment helped reinforce essential data transformation skills using Power Query, preparing raw and messy datasets into structured, analytical-ready formats using industry-standard techniques.




