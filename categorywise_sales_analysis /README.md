
# 📊 Category-wise Sales Analysis with DAX | Power BI

This project showcases how to use advanced DAX functions in Power BI to analyze and visualize category-level sales performance.

---

## 🎯 Objective

The goal of this exercise is to:
- Use **DAX measures** like `CALCULATE()`, `ALL()`, and `ALLEXCEPT()` to control filter context.
- Create a dashboard that shows:
  - The **total sales** across all categories (not affected by filters).
  - The **percentage contribution** of each category.
  - A **card visual** that only responds to **category** filters.

---

## 📁 Dataset

- **File**: `apparels_dataset.xlsx`
- **Columns Used**: `product_name`, `category`, `brand`, `price`, `quantity`, `sale_amount`

---

## 📐 DAX Measures Used

```DAX
-- Category-wise Sales
category_sales = SUM(Sheet1[sale_amount])

-- Total Sales (unaffected by any filter)
total_sales = CALCULATE(SUM(Sheet1[sale_amount]), ALL(Sheet1))

-- Sales by Category (only affected by category filter)
sales_by_category = CALCULATE(SUM(Sheet1[sale_amount]), ALLEXCEPT(Sheet1, Sheet1[category]))
```

---

## 🧮 Visuals Created

| Visual Type | Purpose |
|-------------|---------|
| **Matrix** | Shows `category_sales`, `total_sales`, and `%_contribution` |
| **Card** | Displays total sales by category only |
| **Slicer** | Allows category-wise filtering |

---

## 🖼 Dashboard Preview

![Dashboard Screenshot](https://github.com/ozaairrr/your-repo-name/blob/main/path-to-image.png)

---

## 📝 Notes

> To explore the DAX logic and data model, download the `.pbix` file and check the **Data Model** and **Measure pane**.

---

## 💡 Learnings

- Gained hands-on experience with **filter context management**
- Used `ALL()` to **ignore all filters** and return global totals
- Used `ALLEXCEPT()` to **retain category filters only**
- Learned how visuals behave with **slicers and DAX filters**

---

## 📂 File Structure

```
categorywise-sales-analysis/
│
├── apparels_dataset.xlsx
├── Category_Sales_Dashboard.pbix
├── README.md
└── Dashboard_Screenshot.png
```
