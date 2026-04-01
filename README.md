# E-Commerce Sales Intelligence Report
### Python Analysis + Power BI Dashboard

---

## Why I Built This

In many small and growing businesses — especially across Africa — decisions about what to stock, when to sell, and who your best customers are often come down to gut feeling, experience, or simply watching what competitors do. The data being generated every single day goes unexamined.

I wanted to show that the answers are already there, sitting inside the transaction records. You just need to look.

This project takes a real e-commerce dataset of over one million transactions and asks five simple business questions. The answers turned out to be more interesting than I expected.

---

## What I Found

**Saturday shows minimal activity.**
Looking at the heatmap, Saturday had single digit transactions across almost 
every hour — a stark contrast to the weekday activity. Sunday showed moderate 
activity between 10:00 and 15:00, likely buyers placing orders before the 
work week begins. The busiest single hour across the entire dataset was 
Wednesday at 12:00 with 1,213 transactions.

This pattern — strict business hours, Monday to Friday, near-zero weekends — 
points clearly to a wholesale B2B operation. The customers are retailers, not 
consumers. Marketing and promotions targeting Tuesday to Thursday between 
10:00 and 13:00 would reach the highest concentration of active buyers.

**Two customers. Same number of orders. Very different spend.**
Customers 18102 and 14646 both placed exactly 145 orders. But one spent €608K and the other €526K. When I investigated, the reason was simple — one buys fewer, more expensive items. The other buys enormous quantities of cheaper ones. Same loyalty, completely different buying behaviour. A segmented approach to pricing and account management would better serve both profiles.

**The UK accounts for 85.7% of revenue — from a business selling to 43 countries.**
The UK generates 85.7% of revenue despite the business already operating 
across 43 countries. This concentration suggests that international markets 
— particularly Ireland, Netherlands and Germany which already show consistent 
purchasing — may benefit from targeted marketing investment and optimised 
logistics to support sustainable growth in those regions.

---

## The Data

**Source:** Online Retail II — UCI Machine Learning Repository  
**Period:** November 2009 to December 2011  
**Raw rows:** 1,067,371  
**Clean rows:** 1,037,430  
**Countries:** 43  

---

## What I Did to the Data Before Analysing It

The raw dataset had real problems:

| Problem | How Many Rows | What I Did |
|---------|--------------|------------|
| Cancelled orders mixed with real sales | 19,494 | Removed |
| Negative quantities | 3,457 | Removed |
| Negative prices | 2,750 | Removed |
| "POSTAGE" and "MANUAL" appearing as top products | Several hundred | Investigated StockCodes, then removed |
| Missing Customer IDs | 243,007 (22.77%) | Kept but labelled as Guest |
| Missing descriptions | 4,382 | Dropped |

The postage and manual fee entries were the most interesting catch. They were showing up as top revenue "products" until I checked the StockCodes and realised they were internal charges. Automated cleaning would have missed this entirely — it required actually reading the data.

---

## The Five Business Questions

**Q1. How has revenue trended over time?**  
November is consistently the peak month — nearly 3× the revenue of February. This is a Christmas gifting business. Everything in the product list confirms it.

**Q2. What are the top 10 products by revenue?**  
Regency Cakestand 3 Tier leads at €344K, followed by White Hanging Heart T-Light Holder at €266K. Every single top product is a decorative homeware or seasonal gift item.

**Q3. Which countries generate the most revenue?**  
The UK generates 85.7% (€17.26M). Ireland, Netherlands and Germany show consistent purchasing and may benefit from targeted marketing and optimised logistics to support growth in those regions.

**Q4. When do customers shop?**  
Weekdays between 9am and 5pm. Wednesday at noon is the single busiest hour. Saturday is nearly empty. This shows its not a consumer business — it is wholesale.

**Q5. Who are the top customers?**  
The top two customers by revenue placed the same number of orders but had completely different buying profiles. Revenue alone is not enough to understand your customers.

---

## The Dashboard

The Power BI dashboard has three pages, all interactive and filterable by year.

**Page 1 — Revenue Overview**  
KPI cards showing total revenue, orders, customers and countries. Monthly revenue trend. International revenue by country.

**Page 2 — Products & Countries**  
Top 10 products. International revenue breakdown. UK vs Rest of World split.

**Page 3 — Customers & Patterns**  
Top 10 customers by revenue. Average order value. Guest transactions. Orders by day of week.

📎 [View dashboard PDF](visuals/ecommerceoverview.pdf)

---

## Project Structure

```
ecommerce-sales-analysis/
│
├── data/
│   ├── online_retail_II.csv          ← Raw dataset
│   └── online_retail_clean.csv       ← Cleaned dataset
│
├── notebooks/
│   └── analysis.ipynb                ← Python analysis
│
├── visuals/
│   ├── q1_monthly_revenue.png
│   ├── q2_top_products.png
│   ├── q3_country_revenue.png
│   ├── q4_shopping_heatmap.png
│   └── q5_top_customers.png
│
├── dashboard/
│   └── ecommerce_dashboard.pdf       ← Power BI export
│
└── README.md
```

---

## Tools Used

- Python — Pandas, NumPy, Matplotlib, Seaborn
- Power BI Desktop
- DAX (custom measures)
- Power Query (data transformation)
- VS Code + Jupyter

---


## Technical Note — Power BI Month Sorting

When working with month names in Power BI, the default alphabetical 
sorting (Apr, Aug, Dec...) will misrepresent any time-based trend. 

The fix: create a numeric column (1-12) in Power Query using a 
Conditional Column, then use "Sort by Column" in Data view to force 
MonthName to sort by that number instead.

---

## About

**Bernice Mugure Mathenge**  
Data Scientist · Data Analyst · ML & Analytics Consultant  
📧 bernicemugure29@gmail.com  
🔗 [LinkedIn](https://linkedin.com/in/bernice-mathenge-b17a2b176)
