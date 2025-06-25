## 🐛 Debugging Story: DAX Measure Showing Blank Values in Power BI

### 🎯 Problem

I was working on a Power BI project where I had to calculate the post-invoice deduction amount using the following DAX measure:

```dax
post_invoice_deductions_amount = 
var res = CALCULATE(MAX(post_invoice_deductions[discounts_pct]), 
RELATEDTABLE(post_invoice_deductions))
return res*fact_actuals_estimates[net_invoice_sales_amount]
# 🛠️ Debugging Blank Values in Power BI Despite Correct DAX Formula
---
Even though the formula was correct and working in my mentor’s Power BI file, in my file it was returning blank values in all rows — around **1.67 million (16.7 lakh)** blank rows.

---

## 🔍 Investigation

I started debugging:

- ✅ The relationships between the fact and dimension tables were set up correctly.
- ✅ DAX syntax was valid.
- ❌ But the column still showed blanks.

🧠 I checked my mentor’s version — it had the **same formula**, but it worked perfectly.

---

## 🧪 Root Cause

After inspecting further:

🔎 I checked the `post_invoice_deductions` table in Power BI:

- **My version**: ~2.5 lakh rows  
- **Mentor’s version**: ~20 lakh rows

This immediately raised a red flag.  
So I went back to **MySQL**, where the data was originally imported from, and ran:

```sql
SELECT COUNT(*) FROM post_invoice_deductions;

📉 The count showed only **2.5 lakh records**.

---

## ✅ Fix Applied

- 🔁 Re-imported the **correct complete CSV** into MySQL.
- 🔍 Ran a fresh `COUNT(*)` query — it now showed **20 lakh rows**.
- 🔄 Refreshed the data in **Power BI**.

### 🎉 Result:
The DAX measure started working — returning **correct non-blank values**!

---

## 📘 Key Learnings

- ⚠️ Don’t always blame DAX. Blank values can result from **missing or incomplete data**.
- 📉 `LOOKUPVALUE()` returns **blank** if even one match condition fails.
- 🧾 Always validate **source data completeness** (MySQL, CSVs, APIs, etc.) before troubleshooting DAX formulas.
- ✅ A correct DAX formula won’t help if the **underlying data is not fully loaded**.

