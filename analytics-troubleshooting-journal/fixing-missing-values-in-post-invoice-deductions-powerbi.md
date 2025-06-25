# 🐛 Debugging Story: DAX Measure Showing Blank Values in Power BI
> This story captures a real-world debugging experience I faced while working with Power BI DAX. Even though the formula was correct, the issue was in the data source — a classic example of how not all problems are code-related.

## � Problem

I was working on a Power BI project where I had to calculate the post-invoice deduction amount using the following DAX measure:

```dax
post_invoice_deductions_amount = 
VAR res = CALCULATE(
    MAX(post_invoice_deductions[discounts_pct]),
    RELATEDTABLE(post_invoice_deductions)
)
RETURN
    res * fact_actuals_estimates[net_invoice_sales_amount]
```

Even though the formula was correct and working in my mentor's Power BI file, in my file it was returning blank values in all rows — around 16.7 lakh blank rows.

## 🔍 Investigation

I started debugging:

✅ The relationships between the fact and dimension tables were set up correctly  
✅ DAX syntax was valid  
✅ Tried using slicers and filters on different columns (like customer, product, date) to see if the `post_invoice_deductions_amount` measure would react — it didn’t  
✅ Verified column-level data for the joined tables — everything seemed aligned  
❌ But the `post_invoice_deductions_amount` column still showed blanks

I also checked my mentor's version — it had the **same formula**, but it worked perfectly. This confirmed that the issue was not with DAX syntax, but likely with the data itself.


## 🧪 Root Cause
After inspecting further:

I checked the post_invoice_deductions table in Power BI:

My version: ~2.5 lakh rows

Mentor's version: ~20 lakh rows ❗

This immediately raised a red flag.

So I went back to MySQL where the data was originally imported and ran:

```sql
SELECT COUNT(*) FROM post_invoice_deductions;
The count showed only 2.5 lakh records.
```
## ✅ Fix Applied
🔁 Re-imported the correct complete CSV into MySQL

🔍 Ran a fresh COUNT(*) query — it now showed 20 lakh rows

🔄 Refreshed the data in Power BI

## 🎉 Result:
The DAX measure started working — returning correct non-blank values!

## 📘 Key Learnings
⚠️ Don’t always blame DAX. Blank values can result from missing or incomplete data.

🧾 Always validate source data completeness (MySQL, CSVs, APIs, etc.) before troubleshooting DAX formulas.

✅ A correct DAX formula won’t help if the underlying data is not fully loaded.

## 🙋 What This Story Shows About Me

- I go beyond just writing formulas — I dig into the root cause when things don’t work.
- I understand how DAX behaves in the context of data relationships.
- I validate data from the source, not just from Power BI.
- I document and reflect on my mistakes and solutions to grow as a data professional.
