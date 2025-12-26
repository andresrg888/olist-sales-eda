# Olist E-commerce — Sales Performance EDA

## Executive Summary
This project analyzes sales performance in the Olist e-commerce platform to understand how revenue evolves over time and which product categories and demand patterns drive growth. Using transactional order and item-level data, the analysis focuses on delivered orders only and derives actionable insights relevant to business and product stakeholders.

---

## Business Questions
- How has GMV and order volume evolved over time?
- Is growth driven by pricing (AOV) or demand (number of orders)?
- Which product categories contribute most to GMV?
- Are there signs of revenue concentration across categories?

---

## Dataset
- **Source:** Brazilian E-Commerce Public Dataset by Olist (Kaggle)
- **Timeframe:** 2016–2018
- **Granularity:** Order-level and item-level transactions
- **Key tables used:**
  - orders
  - order_items
  - products
  - product_category_name_translation

Only orders with status `delivered` were considered to ensure revenue reflects completed transactions.

---

## Approach
1. Loaded raw CSV files and validated schema consistency.
2. Converted all timestamp fields to datetime.
3. Filtered dataset to delivered orders only.
4. Joined orders with order items to compute revenue metrics.
5. Derived business metrics:
   - GMV proxy (item price + freight)
   - Orders
   - AOV proxy (mean order GMV)
6. Enriched data with product categories in English.
7. Performed sanity checks on joins and handled missing category translations (~1.4%) by grouping them as `unknown`.

---

## Key Insights
1. GMV grew steadily throughout 2017 and stabilized in 2018.
2. Growth is primarily driven by increased order volume rather than changes in AOV.
3. Order volume shows strong expansion in 2017, indicating demand-led growth.
4. GMV is highly concentrated in a small number of product categories.
5. Health & Beauty and Watches & Gifts are the top revenue-generating categories, while some categories generate high GMV with relatively fewer items, suggesting higher price points.

---

## Visualizations
The following key visualizations were generated:
- Monthly GMV trend
- Monthly Orders trend
- Top 10 categories by GMV

All figures are available in the `reports/` folder.

---

## Recommendations
- Focus growth efforts on demand drivers such as acquisition and repeat purchases rather than pricing changes.
- Prioritize logistics, availability, and assortment quality for top revenue-driving categories.
- Investigate category-level margins to optimize product mix and revenue concentration risk.

---

## Definitions
- **GMV (proxy):** Sum of item price and freight value at order-item level.
- **AOV (proxy):** Mean GMV per order.
- **Delivered orders:** Orders with status `delivered` only.

---

## Limitations & Next Steps
- GMV is a proxy and does not account for refunds or cancellations post-delivery.
- Future analysis could include customer segmentation and regional performance.
- This dataset can be extended into an interactive KPI dashboard and deeper operational analysis.

---

## How to Run
1. Clone the repository.
2. Install dependencies listed in `requirements.txt`.
3. Open the notebook in `notebooks/`.
4. Run `Run → Run All` to reproduce the analysis.
