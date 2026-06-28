# Business Insights Report

**Dashboard:** Retail Executive Dashboard  
**Data Period:** January 2024 – December 2025  
**Analyst Role:** Business Analyst, Retail Leadership Team

---

## Insight 1 – Sales Trend

**Observation:** Sales show a consistent upward trend from early 2024 through late 2025, with noticeable peaks in Q4 of each year (October–December).

**Data Evidence:** Monthly aggregated sales reveal Q4 2025 as the highest revenue period. Total sales over the 2-year period reached ₹217M, with approximately 55–60% generated in 2025 vs 2024.

**Business Interpretation:** The business is growing year-over-year, and Q4 seasonality (likely driven by festive and year-end corporate purchasing) is a reliable demand pattern.

**Recommended Action:** Ensure inventory, staffing, and logistics capacity are scaled up in advance of Q4 each year. Run targeted promotions in Q3 to build momentum into the peak season.

---

## Insight 2 – Regional Performance

**Observation:** The South region leads in both total sales (₹64.7M) and profit (₹10.0M), while East and West are nearly tied at ~₹48.9M each.

**Data Evidence:**
- South: ₹64.7M sales, ₹9.99M profit (15.4% margin)
- North: ₹54.6M sales, ₹8.31M profit (15.2% margin)
- East: ₹48.9M sales, ₹7.60M profit (15.6% margin)
- West: ₹48.9M sales, ₹7.40M profit (15.1% margin)

**Business Interpretation:** South dominates in absolute revenue and profit, but East has a slightly higher profit margin than South. East and West represent growth opportunities where sales volume can be improved without sacrificing margin.

**Recommended Action:** Investigate what drives South's volume advantage (stronger distribution, more customers, larger order sizes?) and replicate those strategies in East and West markets.

---

## Insight 3 – Category Profitability

**Observation:** Technology generates ₹154M in sales with an 18.2% profit margin, making it by far the most profitable category. Furniture has the lowest margin at 6.9%.

**Data Evidence:**
- Technology: ₹153.9M sales, ₹28.0M profit, 18.2% margin
- Office Supplies: ₹11.5M sales, ₹1.7M profit, 14.9% margin
- Furniture: ₹51.6M sales, ₹3.6M profit, 6.9% margin

**Business Interpretation:** Technology is the profit engine of this business. Furniture generates substantial revenue but comparatively low returns, suggesting pricing pressure, high costs, or excessive discounting in that category.

**Recommended Action:** Prioritize Technology expansion and review Furniture's cost structure and discount practices. Consider whether lower-margin Furniture lines are worth continuing or can be repriced.

---

## Insight 4 – Sub-Category Profitability

**Observation:** Within categories, Copiers, Accessories, Phones, and Machines are the top-performing sub-categories. Tables and Bookcases are the worst performers with margins below 6%.

**Data Evidence:**
- Copiers: ₹40.6M sales, 18.0% margin
- Accessories: ₹39.2M sales, 18.3% margin
- Tables: ₹12.9M sales, 5.7% margin
- Bookcases: ₹12.5M sales, 5.7% margin

**Business Interpretation:** The Technology sub-categories (Copiers, Accessories, Phones, Machines) are consistently strong. Tables and Bookcases within Furniture are drag items — high revenue but thin margins — likely due to shipping weight and discount rates.

**Recommended Action:** Conduct a product-level audit of Tables and Bookcases. If margins cannot be improved, consider reducing SKU count or shifting focus to higher-value Furniture items like Chairs.

---

## Insight 5 – Customer Segment Behavior

**Observation:** All three customer segments (Consumer, Corporate, Home Office) show very similar sales volumes (~₹70–75M each), but Home Office generates the highest profit (₹11.6M).

**Data Evidence:**
- Home Office: ₹74.5M sales, ₹11.56M profit, 15.5% margin
- Consumer: ₹71.9M sales, ₹11.03M profit, 15.3% margin
- Corporate: ₹70.6M sales, ₹10.72M profit, 15.2% margin

**Business Interpretation:** Home Office customers, while often overlooked in retail strategy, deliver slightly better profitability. Corporate segment, despite being a key sales target, yields the lowest margin — possibly due to bulk discounts or negotiated pricing.

**Recommended Action:** Design Home Office-specific marketing campaigns and product bundles to grow this segment. Review Corporate pricing agreements and discount caps to protect margins.

---

## Insight 6 – Discount Impact

**Observation:** There is a clear inverse relationship between discount level and profit. Orders with discounts above 30% generate negative average profit (loss of ₹1,601 per order).

**Data Evidence:**
- 0% discount: avg profit ₹13,203 per order
- 1–10% discount: avg profit ₹10,010
- 11–20% discount: avg profit ₹6,336
- 21–30% discount: avg profit ₹3,181
- 31–40% discount: avg profit –₹1,601 (loss)

**Business Interpretation:** Discounting above 30% is actively destroying value. The current discount policy allows discounts up to 35%, which creates a risk zone where the business loses money on individual orders.

**Recommended Action:** Immediately cap maximum discounts at 25–30% as a default policy. Require management approval for any discount above 25%. Train sales staff on the profitability impact of high discounts.

---

## Insight 7 – Shipping & Delivery Performance

**Observation:** Same Day delivery generates the highest average profit per order (₹9,102), while First Class and Standard Class are slightly lower but clustered. Standard Class has the longest average delivery time (4.7 days).

**Data Evidence:**
- Same Day: 0.4 avg delivery days, ₹9,102 avg profit
- First Class: 1.77 days, ₹7,364 avg profit
- Second Class: 2.68 days, ₹8,261 avg profit
- Standard Class: 4.71 days, ₹7,839 avg profit

**Business Interpretation:** Same Day delivery is associated with high-value, high-profit orders (likely Technology products with urgent needs). Standard Class serves a wide range of orders but at lower average profit — partly due to lower-margin product mix.

**Recommended Action:** Investigate whether Same Day delivery is driving profit or if it is the product mix effect. If Same Day customers are more profitable independent of product, consider promoting this option more actively to high-value customer segments.

---

## Insight 8 – Return Patterns

**Observation:** Furniture has a return rate of 7.7%, more than double the Technology rate of 3.0%. Overall return rate is 4.5%.

**Data Evidence:**
- Furniture: 7.67% return rate
- Office Supplies: 3.65% return rate
- Technology: 3.03% return rate

**Business Interpretation:** Furniture's high return rate compounds its already-low margin problem. Returns represent lost revenue, reverse logistics cost, and potential product damage. The category's combination of low margin + high returns makes it a clear risk area.

**Recommended Action:** Investigate root causes of Furniture returns (product quality, inaccurate descriptions, delivery damage?). Improve product photography and dimension information online. Consider stricter quality checks before dispatch for Furniture items.

---

## Calculated Fields Documentation

| Field | Formula | Rationale |
|---|---|---|
| **Profit Margin** | `SUM([Profit]) / SUM([Sales])` | Standard profitability KPI; measures what percentage of revenue becomes profit |
| **Cost** | `SUM([Sales]) - SUM([Profit])` | Derives implied cost since direct cost is not in the dataset; useful for cost benchmarking |
| **Average Order Value** | `SUM([Sales]) / COUNTD([Order ID])` | Measures revenue intensity per transaction; helps identify high-value segments |
| **Return Rate** | `SUM([Return Flag]) / COUNT([Order ID])` | Proportion of orders returned; key risk indicator for product quality and customer satisfaction |
| **Shipping Delay Bucket** | `IF [Delivery Days] = 0 THEN "Same Day" ELSEIF [Delivery Days] <= 2 THEN "Fast (1-2d)" ELSEIF [Delivery Days] <= 4 THEN "Normal (3-4d)" ELSEIF [Delivery Days] <= 6 THEN "Slow (5-6d)" ELSE "Very Slow (7+d)" END` | Groups continuous delivery days into business-meaningful buckets for pattern analysis |
