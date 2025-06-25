# 🐛 Debugging Story: DAX Measure Showing Blank Values in Power BI

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

Even though the formula was correct and working in my mentor's Power BI file, in my file it was returning blank values in all rows — around 16.7 lakh blank rows.

## 🔍 Investigation
I started debugging:

✅ The relationships between the fact and dimension tables were set up correctly

✅ DAX syntax was valid

❌ But the column still showed blanks

I also checked my mentor's version — it had the same formula, but it worked perfectly.

🧪 Root Cause
After inspecting further:

I checked the post_invoice_deductions table in Power BI:

My version: ~2.5 lakh rows

Mentor's version: ~20 lakh rows ❗

This immediately raised a red flag.

So I went back to MySQL where the data was originally imported and ran:

sql
SELECT COUNT(*) FROM post_invoice_deductions;
The count showed only 2.5 lakh records.

✅ Fix Applied
🔁 Re-imported the correct complete CSV into MySQL

🔍 Ran a fresh COUNT(*) query — it now showed 20 lakh rows

🔄 Refreshed the data in Power BI

🎉 Result:
The DAX measure started working — returning correct non-blank values!

📘 Key Learnings
⚠️ Don't always blame DAX. Blank values can result from missing or incomplete data

📉 LOOKUPVALUE() returns blank if even one match condition fails

🧾 Always validate source data completeness (MySQL, CSVs, APIs, etc.) before troubleshooting DAX formulas

✅ A correct DAX formula won't help if the underlying data is not fully loaded

text

You can copy this directly into your GitHub README.md file. The formatting includes:
- Proper headings
- Code blocks with syntax highlighting
- Bullet points
- Emoji icons
- Clear section separation
convert the normal texts into markdown also if you cant then please ads things like # and ## -- --- - which makes the texts get formatted on the readme file
Here's your debugging story converted to proper Markdown format with all text elements properly formatted:

markdown
# 🐛 Debugging Story: DAX Measure Showing Blank Values in Power BI

## 🎯 Problem

I was working on a Power BI project where I had to calculate the post-invoice deduction amount using the following DAX measure:

```dax
post_invoice_deductions_amount = 
VAR res = CALCULATE(
    MAX(post_invoice_deductions[discounts_pct]),
    RELATEDTABLE(post_invoice_deductions)
)
RETURN
    res * fact_actuals_estimates[net_invoice_sales_amount]
Even though the formula was correct and working in my mentor's Power BI file, in my file it was returning blank values in all rows — around 16.7 lakh blank rows.

🔍 Investigation
I started debugging:

✅ The relationships between the fact and dimension tables were set up correctly

✅ DAX syntax was valid

❌ But the column still showed blanks

I also checked my mentor's version — it had the same formula, but it worked perfectly.

🧪 Root Cause
After inspecting further:

I checked the post_invoice_deductions table in Power BI:

Version	Row Count
My file	~2.5 lakh
Mentor's	~20 lakh
This immediately raised a red flag.

So I went back to MySQL where the data was originally imported and ran:

sql
SELECT COUNT(*) FROM post_invoice_deductions;
The count showed only 2.5 lakh records.

✅ Fix Applied
🔁 Re-imported the correct complete CSV into MySQL

🔍 Ran a fresh COUNT(*) query — it now showed 20 lakh rows

🔄 Refreshed the data in Power BI

Result:
🎉 The DAX measure started working — returning correct non-blank values!

📘 Key Learnings
⚠️ Data First: Don't always blame DAX. Blank values can result from missing or incomplete data

📉 LOOKUPVALUE Behavior: Returns blank if even one match condition fails

🧾 Validation: Always verify source data completeness (MySQL, CSVs, APIs) before troubleshooting DAX

✅ Formula ≠ Solution: A correct DAX formula won't help if the underlying data isn't fully loaded

🔍 Comparison Helps: Checking against a working version revealed the data volume discrepancy
