# 📊 Retail Sales Insights Dashboard (Power BI)

## 🚀 Project Overview

This Power BI project blends two rich retail datasets—**Retail Sales Dataset** and **Global Superstore Dataset**—to uncover deep insights into sales performance, customer behavior, and regional trends. This dashboard simulates the responsibilities of a **junior BI analyst** at a mid-sized retail chain.

---

## 🗂️ Datasets Used

### 1. Retail Sales Dataset
- **Fields**: Date, Customer ID, Product Category, Quantity, Price per Unit, Total Amount, Gender, Age
- Source: Kaggle

### 2. Superstore Dataset
- **Fields**: Order Date, Region, Sales, Quantity, Discount, Profit, Product Name, Category, Customer ID
- Source: Kaggle

---

## 🎯 Objectives

- Analyze **monthly and quarterly sales trends**
- Identify **best-performing product categories**
- Compare **revenue across regions**
- Enable **dynamic filtering** based on date, region, and category
- Integrate **multi-source data** with relationships and a shared Date Table

---

## 📀 Data Model & Relationships

| Relationship           | Field 1 (Table A)         | Field 2 (Table B)         | Type         |
|------------------------|---------------------------|----------------------------|--------------|
| Customer ID            | Retail[Customer ID]       | Superstore[Customer ID]    | One-to-Many  |
| Product Category Match | Retail[Product Category]  | Superstore[Category]       | Many-to-Many |
| Shared Date Table      | Retail[Date]              | Superstore[Order Date]     | Many-to-Many |

> A `DateTable` was created using DAX to unify date-based analysis across both datasets.

---

## 🔧 Tools & Technologies

- **Power BI Desktop**
- Power Query (ETL)
- DAX (Data Analysis Expressions)
- Data Modeling & Relationships
- Slicers for dynamic analysis (Date, Region, Product Category)

---

## 🧠 Key DAX Measures

```dax
Total Revenue = SUM('Retail'[Total Amount])
Total Sales = SUM('Superstore'[Sales])
Units Sold = SUM('Retail'[Quantity])
Average Order Value = AVERAGE('Retail'[Total Amount])
Gross Margin = DIVIDE(SUM('Superstore'[Profit]), SUM('Superstore'[Sales]))
Orders Count = COUNTROWS('Retail')
Revenue per Unit = AVERAGE('Retail'[Price per Unit])
Top Region Sales = CALCULATE(SUM('Superstore'[Sales]), ALLEXCEPT('Superstore', 'Superstore'[Region]))
Last Month Sales = CALCULATE([Total Sales], DATEADD('DateTable'[Date], -1, MONTH))
Running Total Revenue = CALCULATE([Total Revenue], FILTER(ALLSELECTED('DateTable'[Date]), 'DateTable'[Date] <= MAX('DateTable'[Date])))
```

---

## 📊 Dashboard Highlights

### ✅ Top-Level KPIs
- Total Revenue
- Units Sold
- Gross Margin %
- Average Order Value

### 📈 Sales Trend (Line Chart)
- Monthly/Quarterly Revenue tracked using a shared `DateTable`

### 📊 Product Category Performance (Bar Chart)
- Visualizes sales by category from both datasets

### 🌍 Region Comparison (Bar / Map)
- Compares regional revenue using `Region` field

### 🎛️ Interactive Filters / Slicers
- 📅 **Date** — Select time range (uses unified `DateTable`)
- 🌍 **Region** — Filter visuals by `Superstore[Region]`
- 🍭 **Product Category** — Works across both datasets
- 👤 **Gender** — Optional demographic filtering (Retail dataset)

---

## 🎨 Design & UX

- Clean, responsive layout using horizontal KPI cards
- Consistent color themes (corporate blue & green for growth metrics)
- Tooltips enabled for detailed insights
- Currency formatting on revenue & profit measures

---

## 📄 Export & Sharing

- 📁 `.pbix` Power BI file available
- 🖼️ Dashboard screenshots attached
- 🚀 Publishable on Power BI Service with interactive filters
- 📄 Exportable as PDF for reporting use cases

---



## 💼 What I Learned

- Blending multiple datasets through shared keys and relationships
- Creating a date dimension for uniform time intelligence
- Writing robust DAX measures for business KPIs
- Designing insightful, user-friendly dashboards
- Setting up meaningful slicers for dynamic exploration



## 📁 Files

```
├── Retail_Sales_Dashboard.pbix
├── datasets/
│   ├── retail_sales_dataset.csv
│   └── Superstore.csv
├── screenshots/
│   ├── dashboard_main.png
│   ├── sales_trend.png
│   └── category_performance.png
└── README.md
```
