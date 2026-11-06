# E-commerce Sales Analysis 2015 (Excel)

An interactive Excel dashboard analysing one year of retail order data, covering sales by product category, seasonality, month-over-month growth, regional performance and the top-selling products.

## Objective
To understand where a retail business's sales come from and when: which categories and products drive revenue, how sales move month to month, and how concentrated revenue is across products, regions and time of year.

## Dataset
- **Source:** Superstore Sales dataset (public sample retail data). Add the link you downloaded it from here, for example `[Kaggle: Superstore Sales Dataset](https://www.kaggle.com/...)`
- **Period used:** 1 Jan 2015 to 31 Dec 2015 (filtered from a multi-year file)
- **Size:** 1,952 order lines, 947 orders, 1,198 distinct products, 3 product categories, 4 regions, 3 customer segments
- **File used:** `superstore_2015_sales.csv`
- **Note:** This is a sample dataset. The version used has **Sales only**, with no Profit or Quantity columns, so profit and margin analysis is not included.

## Workbook structure

| Sheet | Role |
|---|---|
| **Data** | Source table `tblSales`: one row per order line (order, customer, region, category, product, sales) plus helper columns `MonthNo`, `Month`, `Quarter` |
| **Pivots** | Four PivotTables and the PivotCharts built from them |
| **Lists** | Helper ranges that drive the category dropdown and the KPI cards |
| **Dashboard** | Final one-page dashboard with KPI cards, charts, dropdown and slicer |

## Data cleaning and preparation
- Filtered the multi-year file to 2015 and converted dates from day/month/year text to true Excel dates
- Converted the range to an Excel Table (`tblSales`) so formulas and pivots use structured references and update automatically
- Removed **1 fully duplicated row** (a chair order line worth about $281), bringing the total from $479,856 to **$479,575**
- Checked key columns for blanks and set Postal Code to text, since it is an identifier and not a number
- Added helper columns: `MonthNo` (`MONTH`), `Month` (`TEXT`) and `Quarter` (`ROUNDUP`)

## Dashboard

A single-page dashboard with:
- **KPI cards:** Total Sales, Total Orders, Average Order Value, Top Category, Peak Month
- **Monthly Sales by Category:** clustered column PivotChart comparing the three categories across all 12 months
- **Category selector:** a Form Control combo box (Furniture, Office Supplies, Technology) that updates a "Monthly Sales: Selected Category" chart through `INDEX` and `SUMIFS`
- **Top 10 Products:** bar PivotChart ranked by sales, built with a Top 10 value filter
- **Sales and MoM Growth %:** combo chart with monthly sales as columns and month-over-month growth as a line on a secondary axis
- **Region slicer:** filters the PivotCharts by Central, East, South or West

## Key findings

**Overall performance**
1. **Total sales were about $479.6K across 947 orders**, an average order value of about **$506**.
2. **Technology was the top category** at about $173.9K (36.3% of sales), ahead of Furniture (32.6%) and Office Supplies (31.2%). The three categories are close, so no single category dominates.
3. **Top sub-categories were Phones ($77.2K), Chairs ($76.8K) and Machines ($62.0K).**

**Seasonality**
4. **September was the peak month at about $81.6K**, followed by November ($77.9K) and December ($68.2K). These three months produced **47.5% of annual sales**.
5. **Sales are weighted to the end of the year.** Q4 alone made 37.0% of revenue and Q3 29.7%, against 15.4% in Q1 and 17.8% in Q2.
6. **February was the weakest month at about $4.5K**, down 68% from January. Sales then rose about 12x in March ($55.2K), and month-over-month growth swings sharply throughout the year (for example +201% in September and -61% in October).

**Products, regions and customers**
7. **The top product was the Cisco TelePresence System EX90 at about $22.6K**, 4.7% of all sales and roughly twice the revenue of the second-ranked product.
8. **The top 10 products made up 18.5% of total sales.** Across 1,198 products, revenue is spread widely and is not dependent on a handful of items.
9. **The West region led with about $145.9K**, followed by East ($127.4K), South ($103.4K) and Central ($102.9K).
10. **The Consumer segment contributed about $263.0K (55%)**, ahead of Corporate ($127.8K) and Home Office ($88.8K).

## Limitations
- The version of the dataset used has no Profit or Quantity, so findings describe **revenue only**, not profitability.
- Only one year of data is analysed, so seasonality cannot be separated from one-off events such as large single orders. A single high-value product (the Cisco unit) has a visible effect on its month.
- The dataset has 3 product categories and 4 regions. It does not have 4 product categories.
- The category dropdown chart is formula-driven and does not respond to the region slicer.
- This is a sample dataset, so the results illustrate the analysis method and are not about a real company.

## Tools
Microsoft Excel · Excel Tables · PivotTables and PivotCharts · Slicers · Form Controls · 

## How to open
Download `Ecommerce_Sales_Analysis_2015.xlsx` and open it in **desktop Excel** (the combo box is a Form Control and does not work in Excel for the web). Go to the `Dashboard` sheet, use the dropdown to switch the category chart and the slicer to filter by region. If you change the data, use **Data > Refresh All** to update the pivots.
