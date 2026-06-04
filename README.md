<div align="center">

# 📊 Advanced Ecommerce Sales Dashboard

<img src="https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black"/>
<img src="https://img.shields.io/badge/Data_Analysis-Advanced-0078D4?style=for-the-badge&logo=microsoftexcel&logoColor=white"/>
<img src="https://img.shields.io/badge/Records-5009_Orders-6C3483?style=for-the-badge"/>
<img src="https://img.shields.io/badge/Revenue-$2M_Sales-22C55E?style=for-the-badge"/>
<img src="https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge"/>
<img src="https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge"/>

<br/>

> 🚀 A **5-page interactive Power BI dashboard** analyzing **5,009 orders** across **2011–2014**,
> uncovering **$2M in sales**, **$286K profit**, and deep business insights across
> products, customers, regions, and shipping performance.

<br/>

</div>

---

## 📌 Table of Contents

- [Overview](#-overview)
- [Live Dashboard](#-live-dashboard)
- [Dashboard Pages](#-dashboard-pages)
- [Key KPIs](#-key-kpis)
- [Key Insights](#-key-insights)
- [Data Model](#-data-model)
- [Tools & Features](#-tools--features)
- [Project Structure](#-project-structure)
- [How to Use](#-how-to-use)
- [Author](#-author)

---

## 🔍 Overview

The **Advanced Ecommerce Sales Dashboard** is a fully interactive business intelligence solution built in **Power BI Desktop**. It transforms raw ecommerce transaction data into actionable insights for decision-makers across sales, marketing, logistics, and product teams.

**What makes it advanced:**
- 🗂️ **5 dedicated pages** — each focused on a distinct business domain
- 🔗 **Cross-page slicers** — filter by Year, Category, Region simultaneously
- 🗺️ **Interactive map** — drill down to state-level sales performance
- 📐 **Custom DAX measures** — Profit Margin %, YoY Growth, Avg Delivery Days
- 🎨 **Consistent design language** — unified color palette and layout across all pages

---

## 📺 Live Dashboard

> 📂 Open the `.pbix` file in **Power BI Desktop** to explore all interactive features.
> Use slicers to filter by **Year**, **Category**, **Region**, or **Segment**.

---

## 📋 Dashboard Pages

| # | Page | Visuals | Purpose |
|---|------|---------|---------|
| 🏠 | **Home — KPI Overview** | KPI Cards, Trend Sparklines | Orders, Sales, Profit, Margin at a glance |
| 📈 | **Sales Analysis** | Line Chart, Bar Chart | Monthly Sales & Profit trends, Sales by Ship Mode |
| 📦 | **Product Analysis** | Top/Bottom 10 Bar Charts, Treemap | Best & worst products, Profit by Sub-Category |
| 👥 | **Customer Analysis** | Ranked Table, Donut Chart | Top 10 customers, Sales by Segment |
| 🌍 | **Region & Shipping** | Filled Map, Clustered Bars | State-wise sales, Regional profit, Delivery time |

---

## 📊 Key KPIs

<div align="center">

| Metric | Value | Insight |
|--------|-------|---------|
| 🛒 Total Orders | **5,009** | 4-year transaction volume |
| 📦 Total Quantity | **38,000 units** | Items shipped |
| 💰 Total Sales | **$2,000,000** | Gross revenue |
| 💵 Total Profit | **$286,000** | Net earnings |
| 📊 Profit Margin | **12%** | Overall margin rate |
| 🚚 Avg Delivery Days | **3.96 days** | Fulfilment speed |

</div>

---

## 🔑 Key Insights

### 🏷️ Category Performance
```
Technology    ████████████████████  $0.15M profit  ← 🏆 Highest
Furniture     ████████░░░░░░░░░░░░  $0.05M profit
Office Sup.   ██████████████░░░░░░  $0.12M profit
```
- **Technology** leads in profit at **$0.15M** — high-margin products drive bottom line
- **Furniture** has high sales volume but lowest profit margin — pricing opportunity
- **Office Supplies** show consistent, reliable profit year-over-year

### 👥 Customer Segments
```
Consumer      ████████████████████  50.55%  ← Largest segment
Corporate     █████████████░░░░░░░  30.74%
Home Office   ████████░░░░░░░░░░░░  18.71%
```
- **Consumer segment** drives **50.55%** of total sales — primary target audience
- **Corporate accounts** show higher average order value per transaction
- **Home Office** segment is underserved — growth opportunity

### 🌍 Regional Breakdown
```
West     ████████████████████  $108K profit  ← 🏆 Top region
East     ████████████████░░░░  $91K  profit
Central  ████████░░░░░░░░░░░░  $39K  profit
South    ██████░░░░░░░░░░░░░░  $46K  profit
```
- **West region** leads with **$108K profit** — strongest market
- **Central region** underperforms — investigate competition and pricing
- **South** shows recovery potential with focused campaigns

### 🚚 Shipping Analysis
- **Standard Class** is most used — customers prefer cost over speed
- **Same Day** delivery used least — premium pricing limits adoption
- Average delivery time of **3.96 days** is competitive in the market

### 🏅 Top Products
- **Canon imageCLASS** — top seller at **$61,600** in sales
- High-ticket tech items dominate the top 10 revenue list
- Bottom 10 products show negative margins — consider discontinuation

---

## 🗃️ Data Model

```
┌─────────────────────────────────────────────────────────────┐
│                      DATA MODEL                              │
│                                                             │
│  Orders Table (Fact)                                        │
│  ┌──────────────────────────────────────────────────────┐  │
│  │ Order ID │ Date │ Ship Date │ Sales │ Profit │ Qty   │  │
│  └────┬─────┴──┬───┴───────────┴───────┴────────┴───────┘  │
│       │        │                                            │
│       ▼        ▼                                            │
│  ┌─────────┐ ┌──────────┐ ┌──────────┐ ┌──────────────┐   │
│  │Customer │ │ Product  │ │  Region  │ │  Date Table  │   │
│  │Segment  │ │Category  │ │  State   │ │  (Calendar)  │   │
│  │Name     │ │Sub-Cat   │ │          │ │  Year/Month  │   │
│  └─────────┘ └──────────┘ └──────────┘ └──────────────┘   │
└─────────────────────────────────────────────────────────────┘
```

**Key DAX Measures:**
```dax
Profit Margin % = DIVIDE([Total Profit], [Total Sales], 0) * 100

Avg Delivery Days = AVERAGEX(Orders, Orders[Ship Date] - Orders[Order Date])

YoY Sales Growth = 
    DIVIDE([Total Sales] - [Sales PY], [Sales PY], 0) * 100
```

---

## 🛠️ Tools & Features

| Category | Details |
|---|---|
| **Tool** | Power BI Desktop (Latest) |
| **Charts Used** | Line, Bar, Clustered Bar, Donut, Treemap, KPI Cards |
| **Map** | Filled Map (State-level drill-down) |
| **Interactivity** | Cross-page slicers (Year, Category, Region, Segment) |
| **DAX** | Custom measures for Margin %, YoY Growth, Delivery Days |
| **Design** | Unified color palette, consistent layout, icon-based navigation |
| **Data Range** | 2011 – 2014 (4 years, 5,009 orders) |

---

## 📁 Project Structure

```
ecommerce-sales-dashboard/
│
├── 📊 Ecommerce_Sales_Dashboard.pbix    # Main Power BI file
├── 📂 data/
│   └── 📋 ecommerce_orders.csv         # Source dataset
├── 🖼️ screenshots/
│   ├── 01_home_kpi.png                 # KPI Overview page
│   ├── 02_sales_analysis.png           # Sales Analysis page
│   ├── 03_product_analysis.png         # Product Analysis page
│   ├── 04_customer_analysis.png        # Customer Analysis page
│   └── 05_region_shipping.png         # Region & Shipping page
└── 📝 README.md                        # Project documentation
```

---

## 🚀 How to Use

### Step 1 — Prerequisites
- Install **[Power BI Desktop](https://powerbi.microsoft.com/desktop/)** (free)

### Step 2 — Open Dashboard
```
1. Download Ecommerce_Sales_Dashboard.pbix
2. Open with Power BI Desktop
3. Allow data to load (30–60 seconds)
```

### Step 3 — Explore
```
🏠 Start at Home page   → Get overall KPI snapshot
📈 Sales Analysis       → Identify monthly trends & seasonality
📦 Product Analysis     → Find top performers & loss-makers
👥 Customer Analysis    → Understand your best customers
🌍 Region & Shipping    → Spot geographic opportunities
```

### Step 4 — Filter & Interact
```
✅ Use Year slicer       → Compare 2011 vs 2012 vs 2013 vs 2014
✅ Click on a Region     → Cross-filter all visuals on the page
✅ Select a Category     → Drill into Technology / Furniture / Office Supplies
✅ Hover on any chart    → See detailed tooltips
```

---

## 👤 Author

<div align="center">

**Sagar Kishor Shende**
*Data Analytics & AI Enthusiast*

[![GitHub](https://img.shields.io/badge/GitHub-sagar--shende-181717?style=for-the-badge&logo=github)](https://github.com/sagar-shende)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Sagar_Shende-0A66C2?style=for-the-badge&logo=linkedin)](https://www.linkedin.com/in/sagarshende-ai)
[![Email](https://img.shields.io/badge/Email-sagarshende0608@gmail.com-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:sagarshende0608@gmail.com)

</div>

---

<div align="center">

**⭐ Found this useful? Star the repo and share it!**

*Built with 💛 using Power BI · DAX · Data Storytelling*

</div>
