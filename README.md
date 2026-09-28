# Olist Order & Delivery Performance Analysis

## Overview
This project analyzes order-level data from the Olist Brazilian e-commerce 
marketplace to understand fulfillment performance — how orders move from 
purchase through approval, carrier handoff, and final delivery, and where 
delays occur.

**Note on scope:** The original brief asked for product and seller sales 
performance analysis. However, only the `orders` table (order-level data) 
was available — no product, seller, or order-item data. As a result, this 
analysis focuses on delivery and logistics performance rather than 
product/seller sales, and explicitly documents this data limitation.

## Data Source
- Dataset: [Olist Brazilian E-Commerce Public Dataset](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)
- Table used: `orders` (~99,441 rows)
- Fields: order status, purchase/approval/delivery timestamps, estimated 
  delivery date

## Tools Used
- Power BI Desktop (Power Query for transformation, DAX for measures)
- Python/pandas (for data validation)

## Dashboard Structure
1. **Overview** — KPI summary, order volume trend, order status breakdown
2. **Delivery Performance** — delivery time distribution, delay analysis, 
   delivery time vs. delay relationship
3. **Order Status & Funnel** — status breakdown by month/year, cancellation 
   patterns
4. **Approval & Logistics Bottleneck** — time spent in each fulfillment 
   stage (approval, carrier handoff, final delivery)

## Key Findings
- ~97% of orders are successfully delivered; ~0.6% are canceled
- Order volume grew steadily from 2017 into mid-2018
- Average delivery time is ~12.6 days (purchase to customer); most orders 
  deliver within 20 days, though outliers extend to 209 days
- Delivery estimates are conservative — orders arrive ~11 days early on 
  average — but ~8% of delivered orders still arrive later than estimated
- Delivery delay scales closely with delivery duration: longer deliveries 
  are disproportionately likely to run late
- Of the ~12.6-day average fulfillment time, ~9.3 days is carrier-to-customer 
  transit, ~2.8 days is approval-to-carrier handoff, and approval itself 
  takes under a day — carrier transit is the largest single stage
- "Unavailable" orders (609) represent a stock/inventory issue worth 
  further investigation

## Data Caveats
- September–December 2016 and September–October 2018 contain very low 
  order volumes (4–329 orders/month) and were excluded from trend 
  calculations to avoid misleading averages
- This dataset only covers order-level data; product- and seller-level 
  sales analysis (as requested in the original brief) would require the 
  `order_items`, `products`, and `sellers` tables

## Recommendations
- Investigate root causes of long-tail delivery outliers (100+ days)
- Review delivery estimate calibration for orders likely to take longer 
  (e.g., by distance/region), since estimates don't currently adjust for this
- Investigate "unavailable" order status as a potential inventory/stock issue

## Files
- `olist_orders_dashboard.pbix` — Power BI report
- `screenshots/` — dashboard page previews
