# Retail Sales Analytics — Power BI Dashboard

A Power BI dashboard analyzing sales performance across two Australian retail chains (Bellings and Ready Wear), covering ~76K transactions from 2016–2018. Built to explore geographic sales distribution, category performance, gross profit margins, and quarterly trends.

![Dashboard Preview](PowerBI-Dashboard1-Analytics.png)

---

## What This Dashboard Answers

- **Where are sales concentrated?** — Sales by state (NSW leads), with a map visual showing distribution across Australian suburbs
- **How do the two chains compare?** — Ready Wear vs. Bellings breakdown by revenue, category mix, and geographic reach
- **Which categories drive revenue vs. margin?** — Bar chart of sales by category + a scatter plot mapping each category's gross profit % against total sales by quarter
- **What are the quarterly trends?** — Sales and gross profit tracked across FY quarters (2016 Q3 → 2018 Q1), with a combo chart showing revenue vs. margin divergence

---

## Dataset

Single Excel workbook (`retail_analysis.xlsx`) with three sheets:

| Sheet | Rows | Description |
|-------|------|-------------|
| **Fact Table** | 76,467 | Transactional sales data — date, chain, postcode, category, units, sale price, cost price |
| **Aug Data** | 4,497 | August 2017 supplemental data (same schema as Fact Table) |
| **Dim Tables** | 99 | Dimension data — categories/buyers, store locations/managers, and a fiscal calendar |

**Key fields:** Date, Chain (Bellings / Ready Wear), Postcode, Category (Mens, Shoes, Home, Groceries, Kids, etc.), Total Units, Sale Price, Cost Price

---

## Dashboard Components

| Visual | Purpose |
|--------|---------|
| **State slicer** | Filter entire dashboard by Australian state |
| **Sales by Date** | Sparkline with current-period total ($3.18M shown) |
| **Sales by State and Chain** | Clustered bar — geographic revenue split by chain |
| **Sales and Gross Profit by FY Qtr** | Combo chart — revenue bars + profit trend line over time |
| **Sales by Chain** | Pie chart — overall chain revenue share |
| **Sales by Category and Chain** | Stacked bar — which categories each chain is strong in |
| **Sales by State, Country** | Map visual — bubble size represents sales volume by location |
| **GP% vs Sales scatter** | Animated scatter — category-level margin analysis with quarterly playback |

---

## Measures and Calculations

Key DAX measures used in the report:

- **Sales** = `SUM(Total Units * Sale Price)`
- **Cost** = `SUM(Total Units * Cost Price)`
- **Gross Profit** = `Sales - Cost`
- **GP %** = `DIVIDE(Gross Profit, Sales)`

---

## How to Use

**Prerequisites:** [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (free)

1. Clone or download this repo
2. Open `retail_analysis.pbix` in Power BI Desktop
3. The data is embedded in the `.pbix` file — no external connections needed
4. Use the State slicer and scatter plot play axis to explore the data interactively

> If you want to modify the data model, the source Excel file (`retail_analysis.xlsx`) is included.

---

## Repo Structure

```
power-bi-retail-analytics/
├── retail_analysis.pbix      # Power BI report file (open in PBI Desktop)
├── retail_analysis.xlsx      # Source dataset (3 sheets: Fact, Aug Data, Dims)
├── dashboard_preview.png     # Screenshot of the dashboard
├── .gitignore
└── README.md
```

---

## What I'd Extend

- **YoY comparison** — Add a time intelligence measure for same-quarter prior year comparison
- **Profitability deep-dive** — A second report page with margin waterfall by category and chain
- **Store-level drill-through** — Click a postcode bubble on the map → drill into store-level detail
- **Row-level security** — RLS roles for chain-specific access (Bellings managers see only their data)
- **Automated refresh** — Publish to Power BI Service with scheduled refresh from a SQL Server or SharePoint source

---

## Tools

| Tool | Purpose |
|------|---------|
| [Power BI Desktop](https://powerbi.microsoft.com/desktop/) | Report authoring and data modeling |
| Excel | Source data |

---

## License

MIT
