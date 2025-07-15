## 🛠️ Debugging Journal Entry: P&L Net Profit Mismatch – Data Model Issue

### 📅 Date: July 15, 2025  
### 📁 Module: Finance View (Power BI)

### ❓ Problem:
Noticed a mismatch in **Net Profit %** between my dashboard and the benchmark version:
- My version: **-45%**
- Mentor’s version: **-13%**

Also spotted differences in **Operational Expense $** and **row count**.

---

### 🔍 Root Cause:
The `operational_expense` table in my model was **missing relationships** with:
- `fiscal_year`
- `dim_market`

This caused it to **return unfiltered rows**, inflating the total operational expenses and skewing downstream measures like Net Profit and Net Profit %.

---

### 🧪 Troubleshooting Approach:
1. Added a **debug table** with:
   - `Month`
   - `Row Count` from `operational_expense`
   - `Operational Expense $`
2. Compared it **side-by-side with mentor’s debug table**.
3. Found:
   - **113 rows/month** in my table (incorrect)
   - **27 rows/month** in benchmark table (correct)

---

### ✅ Fix:
- Created proper **model relationships** between `operational_expense`, `fiscal_year`, and `dim_market`.
- Immediately saw corrected values across Net Profit, Operational Expenses, and KPIs.

---

### 💡 Lesson Learned:
> Even with perfect DAX formulas, your results will be wrong if the **data model relationships** aren’t correctly set up.  
> Always check for filter context breakdowns using **row count measures** and **debug visuals** when results don’t align.

---

