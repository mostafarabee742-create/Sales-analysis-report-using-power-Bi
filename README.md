# 📊 Sales Analysis Report — Power BI

<div align="center">

![Overview Dashboard](Overview%20page.png)

[![Power BI](https://img.shields.io/badge/Built%20with-Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)](https://powerbi.microsoft.com)
[![DAX](https://img.shields.io/badge/DAX-Advanced%20Measures-CC2927?style=for-the-badge)](.)
[![Pages](https://img.shields.io/badge/Dashboard%20Pages-3-0078D4?style=for-the-badge)](.)
[![Top Category](https://img.shields.io/badge/Top%20Category-Bikes%2096%25-28A745?style=for-the-badge)](.)

> **A 3-page interactive sales analytics dashboard** delivering deep insights into business performance, customer segmentation, and product rankings — empowering decision-makers to monitor sales trends, identify top customers, and optimize product strategy.

</div>

---

## 📊 Dashboard Previews

| Overview | Customer Analysis | Products |
|----------|-------------------|----------|
| ![Overview](Overview%20page.png) | ![Customers](Customers%20page.png) | ![Products](Products%20page.png) |
| Sales, costs & country breakdown | Segmentation & top 10 clients | Product rankings & category performance |

| Data Model |
|------------|
| ![Data Model](Data%20modeling.png) |
| Star schema powering all 3 pages |

---

## 🔍 Project Overview

Sales data without structure is just noise. This dashboard was built to turn multi-year sales records into a clear, navigable story — giving leadership a single place to monitor revenue performance, understand who their best customers are, and know exactly which products are driving the business.

### 🎯 Business Questions Answered
- How are total sales, costs, and orders trending over time?
- Which countries and categories drive the most revenue?
- Who are our top customers — and how are we segmenting them?
- Which products rank highest by sales and orders?
- Where did growth peak and what caused the decline?

---

## 📈 Key Metrics & Highlights

| Metric | Value |
|---|---|
| 🏆 **Top Revenue Category** | Bikes (~96% of total sales) |
| 🌍 **Top Country by Sales** | United States |
| 👥 **Dominant Customer Segment** | New Customers |
| 📅 **Peak Sales Year** | 2013 |
| 📉 **Sales Decline Year** | 2014 |
| 🔟 **Top Customers Tracked** | Top 10 by sales, orders & monthly spend |
| 🔟 **Top Products Tracked** | Top 10 by total sales & total orders |

---

## 🗂️ Dashboard Pages Breakdown

### 📄 Page 1 — Overview
The executive summary of the entire business:

```
💰 Revenue by Category
────────────────────────────────────────
Bikes         →   ~96%   🔴 Dominant
Accessories   →   ~2.5%
Clothing      →   ~1.5%
```

```
🌍 Sales by Country
────────────────────────────────────────
United States    →  🥇 Leader
Australia        →  🥈
United Kingdom   →  🥉
Germany, France, Canada  →  Remaining markets
```

- **Sales by Year:** Clear growth trend peaking in 2013, followed by a notable drop in 2014 — a critical signal for strategic review
- **Orders by Gender:** Gender-based demand split visualized for targeted marketing decisions
- **Subcategory Performance:** Highlights which product subcategories punch above their weight

---

### 📄 Page 2 — Customer Analysis
A full breakdown of who is buying and how they behave:

```
👥 Customer Segments
────────────────────────────────────────
New Customers      →  Largest segment  🟢
Regular Customers  →  Mid-tier loyalty 🟡
VIP Customers      →  Highest value    🔴
```

- **Age Group Distribution:** Sales broken down by age bands — revealing which demographics drive the most revenue
- **Customer Growth Trend:** Year-over-year new customer acquisition vs. retention visualized
- **Top 10 Customers:** Ranked by total sales, number of orders, and average monthly spend
- **Customers by Country:** Geographic customer concentration map for market expansion decisions

---

### 📄 Page 3 — Products Analysis
The product intelligence center:

- **Top 10 Products by Sales:** Which products generate the most revenue
- **Top 10 Products by Orders:** Which products move the most units (volume leaders)
- **Category vs Subcategory Comparison:** Best and worst performing items side by side
- **Revenue Concentration:** Understanding how dependent the business is on a handful of SKUs

---

## 💡 Key Insights & Recommendations

**1. 🚨 96% Revenue Concentration in Bikes is a Risk**
While Bikes are clearly the star product, this level of concentration creates serious business risk. A targeted strategy to grow Accessories and Clothing revenue would build resilience.

**2. 📅 Investigate the 2014 Sales Drop Urgently**
Sales peaked in 2013 then declined in 2014. This could be due to market saturation, competition, pricing changes, or product mix shifts. Understanding the root cause is critical before it repeats.

**3. 🇺🇸 The US is Carrying the Business**
The United States leads all other markets significantly. This is both a strength and a dependency — expanding market share in Australia and the UK could unlock meaningful new revenue.

**4. 👶 New Customers Dominate — Retention is the Priority**
The majority of customers are in the "New" segment, meaning the business is acquiring customers but may be struggling to convert them into Regular or VIP buyers. A loyalty program could be transformational.

**5. 🔟 Top 10 Products Drive Disproportionate Revenue**
A small number of products likely account for a large portion of total sales — classic Pareto principle. Ensuring these products are always in stock, well-marketed, and competitively priced should be a top priority.

**6. 👫 Gender-Based Demand Signals Marketing Opportunity**
The order split by gender opens the door to personalized campaigns — different messaging, products, and channels for different demographics.

---

## 🛠️ Technical Stack

```
📁 Project Structure
├── 📊 project.pbix                  # Main Power BI file (3 pages)
├── 🖼️ Overview page.png             # Page 1 screenshot
├── 🖼️ Customers page.png            # Page 2 screenshot
├── 🖼️ Products page.png             # Page 3 screenshot
├── 🖼️ Data modeling.png             # Data model diagram
└── 📖 README.md
```

### Tools & Technologies
- **Power BI Desktop** — 3-page interactive dashboard
- **DAX** — Advanced KPIs, customer segmentation measures, ranking logic
- **Power Query** — Data cleaning and transformation
- **Data Modeling** — Relationships and star schema architecture

---

## ⚙️ Key DAX Measures Used

```dax
-- Total Sales
Total Sales =
SUM(Sales[SalesAmount])

-- Total Cost
Total Cost =
SUM(Sales[TotalProductCost])

-- Gross Profit Margin
Profit Margin % =
DIVIDE([Total Sales] - [Total Cost], [Total Sales])

-- Customer Segmentation
Customer Segment =
SWITCH(
    TRUE(),
    [Total Orders] >= 10, "VIP",
    [Total Orders] >= 4,  "Regular",
    "New"
)

-- Product Ranking by Sales
Product Rank =
RANKX(ALL(Products[ProductName]), [Total Sales], , DESC, DENSE)

-- Year-over-Year Sales Growth
YoY Sales Growth =
DIVIDE(
    [Total Sales] - CALCULATE([Total Sales], PREVIOUSYEAR('Date'[Date])),
    CALCULATE([Total Sales], PREVIOUSYEAR('Date'[Date]))
)
```

---

## 🚀 How to Use

1. **Clone this repository**
   ```bash
   git clone https://github.com/mostafarabee742-create/Sales-analysis-report-using-power-Bi.git
   ```

2. **Open the dashboard**
   - Install [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (free)
   - Open `project.pbix`

3. **Explore the data**
   - **Page 1 — Overview:** Monitor revenue, costs, and country/category performance
   - **Page 2 — Customers:** Identify top clients and understand segment behavior
   - **Page 3 — Products:** Find your best and worst performing products

4. **Connect your own data** *(optional)*
   - Go to `Transform Data > Data Source Settings`
   - Replace the source with your own sales dataset following the same schema

---

## 🎓 Skills Demonstrated

- **Customer Segmentation** — New, Regular, and VIP classification using DAX
- **Product Ranking** — RANKX-based dynamic top 10 analysis
- **Time Intelligence** — Year-over-year growth tracking and trend analysis
- **Data Modeling** — Star schema with clean relationships across tables
- **Business Intelligence** — Translating multi-year sales data into strategic recommendations
- **Data Visualization** — 3-page storytelling dashboard with cross-filtering

---

## 📬 Contact

**Author:** Mostafa Rabee
**Role:** Data Analyst
**LinkedIn:** [linkedin.com/in/mostafa-rabee74](https://www.linkedin.com/in/mostafa-rabee74)
**Email:** [mostafarabee742@gmail.com](mailto:mostafarabee742@gmail.com)
**GitHub:** [github.com/mostafarabee742-create](https://github.com/mostafarabee742-create)

---

<div align="center">

⭐ **If you found this project useful, please give it a star!** ⭐

*Built with ❤️ by Mostafa Rabee | Data Analyst*
*From Sales Numbers to Business Strategy*

</div>
