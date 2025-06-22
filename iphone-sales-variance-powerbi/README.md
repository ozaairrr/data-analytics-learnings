
# 📊 iPhone 14 vs iPhone 15 Sales Comparison (Power BI Project)

This project is a Power BI-based sales comparison dashboard between iPhone 14 and iPhone 15. The objective was to analyze, compare, and report sales performance across different countries using calculated metrics and visuals.

---

## 🧠 Objective

Conduct a **comparison analysis** of iPhone 15 sales and iPhone 14 sales using three datasets:

- `fact_sales_Iphone14.csv`
- `fact_sales_Iphone15.csv`
- `dim_stores.csv`

---

## 📌 Tasks Performed

1. **Reviewed and cleaned datasets**
   - Merged iPhone 14 & 15 sales data using `store_id` and `month`
   - Joined with `dim_stores` to bring in `country_name`

2. **Calculated metrics**
   - iPhone 14 total sales
   - iPhone 15 total sales
   - 🔸 **Absolute Variance** = `ABS([iPhone15 Sales] - [iPhone14 Sales])`
   - 🔸 **% Variance** = `([iPhone15 Sales] - [iPhone14 Sales]) / [iPhone14 Sales] * 100`

3. **Created DAX Measures**
   - Used `SUM`, `ABS`, and `DIVIDE` to build dynamic calculations grouped by country
   - Demonstrated difference between **Power Query row-level logic** and **DAX context-based aggregation**

4. **Built final dashboard**
   - Table view with: Country, iPhone14 Sales, iPhone15 Sales, Absolute Variance, % Variance
   - Bar chart of top 10 countries by sales variance
   - KPI cards showing absolute variance and % variance between sales.

---

## 📊 Sample Visual

![Dashboard Screenshot](.![image](https://github.com/user-attachments/assets/9546bad8-03fb-429e-8c9f-9be16d86a6f8))

---

## 🧰 Tools Used

- **Power BI Desktop**
- **Power Query**
- **DAX (Data Analysis Expressions)**

---

## 🎯 Key Learnings

- Practiced merging datasets with relationship keys (store_id, month)
- Understood difference between Power Query row operations and DAX aggregation
- Applied real-world business logic: sales comparison, variance reporting
- Learned how to visualize insights clearly through tables, bar charts, and KPI cards

---

## 📁 Files Included

| Folder         | Description                          |
|----------------|--------------------------------------|
| `/data`        | Contains the original CSV datasets   |
| `/screenshots` | Screenshot of the final Power BI dashboard |
| `/pbix-file`   | Power BI project file (.pbix)        |
| `README.md`    | Project overview and documentation   |

