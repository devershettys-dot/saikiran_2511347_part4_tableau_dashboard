# Retail Executive Dashboard – Tableau Project

## 1. Business Problem Summary

The retail leadership team needs a centralized executive dashboard to monitor and act on key business performance areas: sales trends, profitability, regional performance, customer segment behavior, category-level results, shipping efficiency, discount impact, and return patterns. The goal is to enable data-driven decision-making by surfacing both opportunities and risks in a single, interactive Tableau dashboard.

---

## 2. Dataset Description

**File:** `dashboard_sales_data.xlsx`  
**Sheet:** `dashboard_sales_data`  
**Rows:** 4,200 orders  
**Date Range:** January 1, 2024 – December 31, 2025 (2 full years)

| Field | Type | Description |
|---|---|---|
| order_id | String | Unique order identifier |
| order_date | Date | Date the order was placed |
| ship_date | Date | Date the order was shipped |
| customer_id | String | Unique customer identifier |
| customer_segment | Categorical | Consumer, Corporate, Home Office |
| region | Categorical | North, South, East, West |
| state | Categorical | 19 Indian states |
| city | Categorical | City of the customer |
| category | Categorical | Furniture, Office Supplies, Technology |
| sub_category | Categorical | 13 sub-categories |
| product_name | String | Product name |
| ship_mode | Categorical | Same Day, First Class, Second Class, Standard Class |
| sales | Numeric (₹) | Revenue per order line |
| quantity | Integer | Units ordered |
| discount | Numeric (%) | Discount applied (0 to 0.35) |
| profit | Numeric (₹) | Profit per order line |
| return_flag | Binary (0/1) | 1 = returned order |
| delivery_days | Integer | Days from order to ship (0–9) |
| customer_rating | Numeric | Customer satisfaction score (1–5) |
| campaign_channel | Categorical | Organic, Social, Paid, Email, Referral, (some null) |

**Assumptions & Notes:**
- `delivery_days` is calculated as ship_date minus order_date; 0 = Same Day delivery.
- `return_flag = 1` means the order was returned; return rate = ~4.5% overall.
- ~2% of `campaign_channel` values are null; treated as "Unknown" channel in analysis.
- Dates were stored as Excel serial numbers and correctly parsed by Tableau/pandas as dates.
- All monetary values are in Indian Rupees (₹).

---

## 3. Tableau Workbook Description

The Tableau packaged workbook (`RetailDashboard.twbx`) contains:
- **7 individual sheets** covering sales trend, regional performance, category profitability, customer segments, shipping performance, discount vs profit, and return analysis
- **1 executive dashboard** combining all key views with KPI cards, filters, and filter actions
- **5+ calculated fields** documented below

---

## 4. Calculated Fields Created

| Field Name | Formula | Purpose |
|---|---|---|
| Profit Margin | `SUM([Profit]) / SUM([Sales])` | Shows profitability as a percentage of revenue |
| Cost | `SUM([Sales]) - SUM([Profit])` | Derives cost from sales and profit |
| Average Order Value | `SUM([Sales]) / COUNTD([Order ID])` | Average revenue per unique order |
| Return Rate | `SUM([Return Flag]) / COUNT([Order ID])` | Proportion of orders that were returned |
| Shipping Delay Bucket | `IF [Delivery Days] = 0 THEN "Same Day" ELSEIF [Delivery Days] <= 2 THEN "Fast (1-2d)" ELSEIF [Delivery Days] <= 4 THEN "Normal (3-4d)" ELSEIF [Delivery Days] <= 6 THEN "Slow (5-6d)" ELSE "Very Slow (7+d)" END` | Categorizes delivery speed for analysis |

---

## 5. Dashboard Components

The executive dashboard includes:

**KPI Cards (top row):**
- Total Sales (₹217M)
- Total Profit (₹33.3M)
- Overall Profit Margin (15.3%)
- Return Rate (4.5%)

**Charts:**
1. Sales Trend (line chart – monthly over 2 years)
2. Regional Performance (bar chart – sales & profit by region)
3. Category Profitability (bar chart – category and sub-category)
4. Customer Segment Comparison (bar chart – sales/profit by segment)
5. Shipping Performance (bar chart – delivery days by ship mode)
6. Discount vs Profit (scatter plot – order-level discount vs profit)
7. Return Analysis (bar chart – return rate by category and segment)

---

## 6. Filters and Interactions Used

**Filters applied to dashboard:**
- Region (dropdown)
- Category (multi-select)
- Customer Segment (multi-select)
- Order Date (date range slider)
- Ship Mode (dropdown)
- Campaign Channel (dropdown)

**Interactions:**
- Clicking a region in the Regional Performance chart filters all other views (filter action)
- Clicking a category bar highlights sub-category detail
- Date slider dynamically updates all KPI cards and charts

---

## 7. Key Business Insights

See `outputs/business_insights.md` for the full set of 8+ structured insights. Summary:

- **Technology** drives 70.9% of all profit despite representing ~71% of sales revenue — highest margin category at 18.2%
- **South region** is the top performer by both sales and profit
- **Furniture** has the highest return rate (7.7%) and lowest margin (6.9%) — risk area
- **Discounts above 30%** result in negative average profit — discount policy needs review
- **Same Day** shipping generates the highest average profit per order (₹9,102)
- **Home Office** segment is the most profitable despite similar sales volume to others

---

## 8. Dashboard Story Summary

See `outputs/dashboard_story.md` for the full narrative. The dashboard tells a story of a business with strong Technology performance, a risky Furniture segment, regional growth opportunities in the East, and a discount strategy that needs tightening above the 30% threshold.

---

## 9. Assumptions and Limitations

- Data covers only 2024–2025; seasonal patterns may not be fully established
- `campaign_channel` has ~2% null values — these orders are excluded from channel analysis
- Customer IDs are present but no demographic data is available for deeper segmentation
- Return reasons are not captured — we know what is returned but not why
- Profit is order-level; overhead/fixed costs are not reflected
- City/state geographic mapping assumes Indian geography

---

## 10. Screenshots Included

| File | Contents |
|---|---|
| `screenshots/full_dashboard.png` | Complete executive dashboard |
| `screenshots/sales_trend_view.png` | Sales trend line chart sheet |
| `screenshots/regional_performance_view.png` | Regional bar chart sheet |
| `screenshots/category_profitability_view.png` | Category/sub-category profitability sheet |
| `screenshots/filter_interaction_view.png` | Dashboard showing active filter interaction |
