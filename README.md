# ☕ Tim Hortons Business Performance Dashboard
An end-to-end Power BI project analyzing sales, profitability, customer behavior, and store performance for a simulated Tim Hortons retail network across Canada — built as a portfolio case study by Akash Gahlot.

 Tim.Hortans.Video.mp4 
# 📌 Project Overview
This project simulates a full Business/Data Analyst workflow: taking raw transactional sales data, modeling it into a clean star schema, and building a multi-page interactive Power BI dashboard that surfaces revenue, profitability, customer, and geographic insights for stakeholders.

### Business questions this dashboard answers:

How is revenue and profit trending over time, and which stores/categories drive it?
Which products are the top revenue and profit generators?
How do new vs. returning customers behave, and what drives retention?
Which regions, provinces, and cities are the strongest and weakest performers?
When (day of week / time of day) do customers order the most?

# 🗂️ Dataset
File: Tim_Hortons_Portfolio_Dataset.xlsx
Rows: ~17,445 transactions
Grain: One row per order line item
The dataset spans stores in Toronto (Downtown & North), Montreal, Vancouver, Ottawa, and Calgary, across five product categories: Coffee, Sandwich, Bakery, Tea, and Desserts.

# 🧩 Data Model
A star schema was built in Power Query / Power BI to support efficient, scalable analysis:

<img width="1443" height="788" alt="Screenshot 2026-08-29 140538" src="https://github.com/user-attachments/assets/0a543a26-bd55-421d-b7a1-17184ce4e5f1" />


**SalesData (fact table)** — transaction-level revenue, cost, profit, and discount

**DimDate** — full date hierarchy (day, day name, month, weekend flag) for time intelligence

**DimStore / Total Store** — store and city reference

**DimLocation** — city, province, and region mapping for geographic rollups

**DimProduct** — category and product reference

This structure enables clean, reusable relationships across all report pages and supports DAX measures like profit margin, retention %, and average order value.



# 📊 Dashboard Pages
1. Executive Overview




2. Product & Category Analysis




3. Customer & Sales Behavior



4. **Store & Geographic Analysis**

<img width="1907" height="979" alt="Screenshot 2026-08-31 150610" src="https://github.com/user-attachments/assets/6d4d2ef2-1ded-42d1-9ea7-6fcf8562d78b" />



All pages include interactive slicers for Month, Region, Store, Category, and Customer Type, allowing dynamic filtering across the entire report.

## 📐 Key DAX Measures
**Total Revenue**         := SUM(FactSales[Revenue])

**Total Profit**         := SUM(FactSales[Profit])

**Total Orders**          := DISTINCTCOUNT(FactSales[OrderID])

**Total Quantity**        := SUM(FactSales[Quantity])

**Average Order Value**   := DIVIDE([Total Revenue], [Total Orders])

**Profit Margin %**       := DIVIDE([Total Profit], [Total Revenue])

DIVIDE() is used instead of the / operator throughout to avoid divide-by-zero errors when slicers filter data down to nothing.

DISTINCTCOUNT is used for Total Orders (rather than a simple row count) because a single order can span multiple line items — one row per product, not per order.

## ✨ Dashboard Features
**4-page interactive report** — Executive Overview, Product & Category Analysis, Customer & Sales Behavior, and Store & Geographic Analysis

**Cross-page slicers** — Month, Region, Store, Category, and Customer Type filters that dynamically update every visual on the page

**Custom KPI cards** — Revenue, Profit, Orders, Units Sold, and Profit Margin surfaced at a glance on every page

**Time intelligence** — revenue trends by month, day of week, and hour of day using the DimDate table

**Geographic visuals** — map-based revenue by province, revenue heatmap by city, and regional performance comparisons

**Customer analytics** — new vs. returning segmentation, retention trend over 12 months, and revenue by payment method

**Custom-branded UI** — Tim Hortons–themed color palette, iconography, and page navigation designed for a polished, stakeholder-ready look

**Fully responsive filtering** — all measures use DIVIDE() and DISTINCTCOUNT patterns so KPIs stay accurate under any slicer combination, including edge cases where filters return no data

## 🔑 Key Insights

**Total Revenue**: $254.58K | **Total Profit**: $95.61K | **Profit Margin**: 37.6%

Coffee is the dominant category, generating $131.62K in revenue — more than 2x the next closest category (Sandwich, $45.40K)

Cappuccino, Cold Brew, and Americano are the top 3 products by both revenue and profit

Toronto Downtown is the top-performing store at $89K revenue, nearly double the next store

Returning customers drive the majority of revenue ($164.51K vs. $90.07K from new customers), with retention holding steady around 50–60% monthly

Saturday is the highest-revenue day; afternoon (12 PM–3 PM) is the peak ordering window

Central region (Toronto/Montreal/Ottawa) contributes $201.40K vs. $53.18K from the West (Vancouver/Calgary)

## 🛠️ Tools & Skills
**Power BI Desktop** — data modeling, DAX measures, interactive report design

**Power Query** — data cleaning and transformation

**Excel** — source data structuring

**DAX** — calculated KPIs (Profit Margin, Retention %, Avg. Order Value, Avg. Customer Spend)

Dashboard UI/UX design (custom Tim Hortons–themed branding, navigation, and layout)


## 👨‍💻 About Me

I'm an aspiring Business Analyst passionate about transforming data into actionable insights through interactive dashboards, business intelligence, and data storytelling.

⭐ If you found this project helpful...
Consider giving it a ⭐ Star on GitHub.

It motivates me to build and share more Business Intelligence and Data Analytics projects.
