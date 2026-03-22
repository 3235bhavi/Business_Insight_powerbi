# Business Insights 360 — AtliQ Hardware | Power BI Dashboard

## 📌 Project Overview

AtliQ Hardware is a fast-growing global electronics company operating across **27 markets** and serving **75+ customers** worldwide. Despite strong revenue growth, the company was consistently reporting **net losses** and leadership had no clear visibility into why.

All decisions were being made using Excel sheets and gut feeling. This approach failed badly when AtliQ expanded into Latin America and incurred heavy losses a market entry that could have been avoided with proper data analysis.

**The core business question I set out to answer:**
> *The company grew revenue by 373% year-over-year so why is Net Profit still at -14.13%?*

To answer this, I built **Business Insights 360** a 6-view interactive Power BI dashboard that gives every department (Finance, Sales, Marketing, Supply Chain, Executive and Products) a single source of truth for their KPIs.

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| Power BI Desktop | Dashboard design and visualisation |
| DAX | KPI measures and calculated columns |
| Power Query | Data cleaning and transformation |
| MySQL | Source data extraction |
| Excel | Secondary data source |
| DAX Studio | Report performance optimisation |
| Power BI Service | Publishing and auto-refresh |

---

## 📂 Data Sources

- **MySQL Database** - Sales transactions, customer master, product master, market data
- **Excel Files** — Targets, operational expenses, market share data
- **Total Records** — 1 Million+ rows across fact and dimension tables
- **Time Period** — FY 2018 to 2022 (Estimated)
- **Data Refresh** — Automated monthly refresh on 5th working day via Power BI Service

---

## 📐 Data Model

Built a **Star Schema** with:
- Fact tables: fact_sales_monthly, fact_forecast_monthly
- Dimension tables: dim_customer, dim_product, dim_market, dim_date
- Connected MySQL and Excel sources using Power Query
- Established relationships between all fact and dimension tables for accurate cross-filtering

---

## 📊 Dashboard Views

### 🏠 Home Page
Navigation hub with buttons linking to all 6 views. Shows data load date and currency information. Designed for ease of use across all departments.

---

### 1️⃣ Finance View

**Business Question:** Where is the money going and why is profit negative despite strong revenue?

**KPIs Tracked:**
- Net Sales, Gross Margin %, Net Profit %
- Year-over-year and vs Target comparisons

**Key Charts:**
- Full P&L Statement (Gross Sales → Deductions → Net Sales → COGS → GM → OpEx → Net Profit)
- Net Sales performance trend over time
- Top and bottom performing customers and products by Net Sales
- Regional P&L breakdown (APAC, EU, NA, LATAM)

**Key Finding:**
> Net Sales in 2021 were $823.85M — up 207% vs last year. But Net Profit was -6.63%. The P&L drill-down revealed that **$448M was lost to Pre and Post Invoice Deductions** before revenue was even recognised. Then **Operational Expenses of $355M** wiped out the remaining Gross Margin. The company wasn't failing to sell it was failing to retain what it sold.

---

### 2️⃣ Sales View

**Business Question:** Which customers are actually profitable not just high revenue?

**KPIs Tracked:**
- Net Sales, Gross Margin $, Gross Margin %
- Customer-level and product-level performance

**Key Charts:**
- Customer Performance table (NS$, GM$, GM%)
- Performance Matrix — GM% vs Net Sales (identifies high revenue but low margin customers)
- Unit Economics donut — COGS vs Gross Margin breakdown
- Product segment performance table

**Key Finding:**
> **Amazon** was the top customer at **$278.66M revenue** but had only **37.24% GM%** below the company average of 38.35%. Meanwhile **AtliQ Exclusive** generated $201.80M at **46.16% GM%** nearly 9 points healthier. The Performance Matrix clearly showed Amazon in the high-revenue but below-average-margin zone. Reducing Amazon's discount structure by even 2-3% would significantly improve overall profitability.

---

### 3️⃣ Market View

**Business Question:** Is the profit problem specific to certain products or is it a company-wide cost issue?

**KPIs Tracked:**
- Net Sales, Gross Margin %, Net Profit % by product segment
- Regional and market-level profitability

**Key Charts:**
- Product Performance table (NS$, GM$, GM%, Net Profit$, Net Profit%)
- Performance Matrix — Net Profit% vs Net Sales by division
- Region/Market/Customer performance breakdown
- Unit Economics — COGS vs GM with operational expense waterfall

**Key Finding:**
> Every single product segment showed **negative Net Profit** — Notebooks (highest revenue at $897.19M) lost $124.93M. Accessories, Desktop, Peripherals and Storage all in the red. APAC — the largest region at $1.04B still reported -14.22% Net Profit. This ruled out a product-specific problem. When every segment fails simultaneously, it is a **cost structure problem** — operational expenses are too high relative to gross margin across the board.

---

### 4️⃣ Supply Chain View

**Business Question:** Is poor demand forecasting adding to costs through excess inventory or lost sales?

**KPIs Tracked:**
- Forecast Accuracy %, Net Error, ABS Error
- Customer and product-level forecast performance
- Risk classification (EI = Excess Inventory, OOS = Out of Stock)

**Key Charts:**
- Forecast Accuracy vs Net Error trend (monthly)
- Customer-wise forecast accuracy and risk table
- Product segment forecast accuracy and risk table

**Key Finding:**
> Forecast Accuracy was **81.17%** which looks acceptable. But the **Net Error was -3,472.7K** meaning the company was consistently under-forecasting demand. Yet almost every customer in the table showed **EI (Excess Inventory)** risk. This contradiction revealed a **distribution mismatch** the wrong products were being sent to the wrong markets. Fast-moving products were running out (OOS) while slow-moving products piled up (EI) in the same warehouses. Networking had 93% forecast accuracy yet was still OOS — supply couldn't keep up with correctly predicted demand.

---

### 5️⃣ Executive View

**Business Question:** What is the overall health of the business and where are the biggest risks?

**KPIs Tracked:**
- Net Sales, Gross Margin %, Net Profit %, Forecast Accuracy %
- Market share vs competitors (Dell, HP, Lenovo, Innovo, Pacer)
- Revenue by Division and Channel

**Key Charts:**
- Top-level KPI cards with benchmark comparisons
- Subzone performance table with risk flags (EI/OOS)
- PC Market Share Trend — AtliQ vs competitors (2018–2022)
- Revenue by Division donut (PC 58.68%, P&A 26.69%, N&S)
- Revenue by Channel donut (Retailer 71.59%, Direct, Distributor)
- Top 5 Customers and Top 5 Products by revenue

**Key Finding:**
> Net Sales hit **$1.64B in 2022EST** up 373% vs benchmark but **Net Profit was still -14.13%**. India, the largest subzone at $445.3M, had -23.1% Net Profit and OOS risk. LATAM and NA both flagged Excess Inventory. AtliQ's **market share was 5.9%** growing but significantly behind Dell and competitors. PC segment drove **58.68% of all revenue** and Retailers accounted for **71.59% of all sales** both represent dangerous concentration risks if either shifts.

---

## 💡 Final Business Recommendations

Based on the complete dashboard analysis, here are the data-driven recommendations:

1. **Fix the discount structure** — Post Invoice Discounts are the single biggest margin leak. Renegotiate terms with high-volume low-margin customers, starting with Amazon.

2. **Reduce operational expense ratio** — OpEx is consuming all Gross Margin. Target OpEx below 25% of Net Sales to achieve positive Net Profit.

3. **Rebalance supply chain distribution** — Stop measuring only overall Forecast Accuracy. Track product-market level distribution to eliminate the EI+OOS paradox happening simultaneously.

4. **Diversify customer and channel mix** — 71.59% Retailer dependency and Amazon's outsized share are concentration risks. Grow AtliQ Exclusive and direct channels which show healthier margins.

5. **Prioritise India market profitability** — Largest subzone by revenue but -23.1% Net Profit. Fix pricing and cost structure here first before expanding further.

---

## ⚙️ DAX Measures Created

```
Net Profit % = DIVIDE([Net Profit], [Net Sales]) * 100

Gross Margin % = DIVIDE([Gross Margin], [Net Sales]) * 100

Forecast Accuracy % = 
    1 - DIVIDE(ABS([Net Error]), [Total Forecast Qty])

Net Error = [Total Forecast Qty] - [Total Sales Qty]

Post Invoice Deduction % = 
    DIVIDE([Post Invoice Deductions], [Gross Sales]) * 100
```

---

## 📸 Dashboard Screenshots

| View | Preview |
|---|---|
| Home |<img width="974" height="554" alt="Home" src="https://github.com/user-attachments/assets/e3027fd4-dc08-4cb2-b025-94eb074d2cb5" />|
| Finance |<img width="970" height="554" alt="Finance View" src="https://github.com/user-attachments/assets/e19428fd-9535-4829-9c57-a2e3d250c1fa" />|
| Sales | ![Sales](<img width="993" height="563" alt="Sales View" src="https://github.com/user-attachments/assets/3cb2a304-e601-4053-a186-36b2a6264311" />
) |
| Market |<<img width="994" height="558" alt="Market View" src="https://github.com/user-attachments/assets/09e9054c-5931-483b-9239-0b385ab72ab2" />
 />|
| Supply Chain |<<img width="992" height="562" alt="Supply Chain View" src="https://github.com/user-attachments/assets/fe416762-eccd-49a4-9fa3-047d738ddc06" />
/>|
| Executive |<<img width="999" height="564" alt="Executive view" src="https://github.com/user-attachments/assets/35a16345-91ae-42a5-bf11-f0acd53f0c0d" />
 /> |

---

## 🎯 Skills Demonstrated

- Data modeling (Star Schema) across MySQL and Excel sources
- DAX measure writing for business KPIs
- Report performance optimization using DAX Studio
- Translating business problems into analytical questions
- Cross-functional dashboard design (Finance, Sales, Supply Chain, Executive)
- Publishing and scheduling data refresh on Power BI Service

---

## 👤 About Me

**Bhavi Jain** — Data Analyst | Power BI • SQL • Excel

📧 jainbhavi50@gmail.com
🔗 [LinkedIn](https://linkedin.com/in/bhavi-j-7b7951250)
💻 [GitHub Portfolio]([https://github.com/3235bhavi/Business_Insight_powerbi])



