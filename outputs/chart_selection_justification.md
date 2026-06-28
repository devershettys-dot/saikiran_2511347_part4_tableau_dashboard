# Chart Selection Justification

**Dashboard:** Retail Executive Dashboard  
**Principle:** Every chart answers a specific business question. Chart type is chosen to match the nature of the data and the decision it supports.

---

## 1. Sales Trend View — Line Chart

**Business Question:** How are total sales changing over time? Are we growing month-over-month?

**Why this chart type:** A line chart is the standard for continuous time-series data. It allows the viewer to see direction, momentum, and seasonal peaks at a glance. A bar chart would work but creates visual clutter across 24 months; a line connects the trend clearly.

**Fields used:**
- X-axis: Order Date (truncated to Month)
- Y-axis: SUM(Sales)
- Optional dual-axis: SUM(Profit) on secondary axis with different color

**Design principle applied:** Minimal clutter — only two lines maximum, no gridline excess. Labels on peak points only. Title clearly states "Monthly Sales Trend."

**Mistake avoided:** Did not use an area chart with fill (hides secondary metrics and distorts scale perception).

---

## 2. Regional Performance View — Horizontal Bar Chart

**Business Question:** Which region performs best on sales and profit? Where should we focus investment?

**Why this chart type:** A horizontal bar chart makes region-name labels easy to read without rotation. Bars allow direct size comparison between regions. A map was considered but India's region groupings (North/South/East/West) don't align well with state-level map encoding.

**Fields used:**
- Rows: Region
- Columns: SUM(Sales), SUM(Profit) — side-by-side bars
- Color: Distinct region colors (consistent across dashboard)

**Design principle applied:** Bars sorted descending by Sales so the highest-performing region appears first. Profit Margin shown as a label tooltip.

**Mistake avoided:** Did not use a pie chart — pies are poor for comparing more than 3 values and make it hard to read absolute differences.

---

## 3. Category Profitability View — Bar Chart with Sub-category Drill-down

**Business Question:** Which categories and sub-categories drive profit or losses?

**Why this chart type:** A grouped/stacked bar chart at the category level, expandable to sub-category, allows comparison of both absolute profit and relative size. A treemap was also considered (and is an alternative view) but bar charts are easier to compare across specific values.

**Fields used:**
- Rows: Category → Sub-category (hierarchy)
- Columns: SUM(Profit)
- Color: Profit (diverging color scale — blue for positive, orange/red for negative)

**Design principle applied:** Diverging color scale immediately draws the eye to negative-profit sub-categories. Sorted by profit descending within each category.

**Mistake avoided:** Did not use a single-color bar chart — the diverging scale is essential here because some sub-categories have negative profit, which is the key insight.

---

## 4. Customer Segment View — Bar Chart

**Business Question:** Which customer segment generates the most revenue and profit? How do segments compare on margin?

**Why this chart type:** Three segments with three metrics (Sales, Profit, Margin) maps cleanly to a grouped bar chart. A highlight table was considered but bar charts are more intuitive for a leadership audience unfamiliar with Tableau.

**Fields used:**
- Rows: Customer Segment
- Columns: SUM(Sales), SUM(Profit)
- Label: Profit Margin % on bar end
- Color: Consistent segment color (matches other views)

**Design principle applied:** Consistent color palette across all segment-related views so leadership can follow the same segment across charts without re-reading legends.

**Mistake avoided:** Did not encode segments with 3 different hues that might imply ranking — segments are nominal, not ordinal.

---

## 5. Shipping Performance View — Bar Chart + Reference Line

**Business Question:** Which shipping mode causes delays? How does delivery time vary by ship mode?

**Why this chart type:** A horizontal bar chart comparing average delivery days by shipping mode is clean and direct. A reference line at the company's target SLA (e.g., 3 days) makes the gap immediately visible.

**Fields used:**
- Rows: Ship Mode
- Columns: AVG(Delivery Days)
- Color: Shipping Delay Bucket (calculated field — green = fast, red = slow)
- Reference line: Target delivery threshold

**Design principle applied:** Color encodes urgency — slow modes appear in warmer colors. Bars sorted by delivery days so the worst performers are obvious.

**Mistake avoided:** Did not use a line chart (no temporal dimension here — these are averages by category, not a trend).

---

## 6. Discount vs Profit View — Scatter Plot

**Business Question:** How does the level of discount on an order relate to the profit generated?

**Why this chart type:** A scatter plot is the only chart type that can show the relationship (correlation) between two continuous numerical variables at the order level. Each point represents one order. The negative trend (more discount = less profit) is visually obvious in scatter form.

**Fields used:**
- X-axis: Discount (continuous, 0–0.35)
- Y-axis: Profit (continuous)
- Color: Category (to show which categories cluster in high-discount zones)
- Reference line: Profit = 0 (highlights orders where discount causes loss)

**Design principle applied:** A zero-profit reference line is essential — it visually separates profitable orders from loss-making ones. Points above the line are healthy; below the line is a danger zone.

**Mistake avoided:** Did not use a bar chart of average discount by category — that would hide the individual order-level story and the spread of outcomes.

---

## 7. Return Analysis View — Bar Chart

**Business Question:** Which categories and segments have the highest return risk?

**Why this chart type:** A bar chart showing Return Rate (calculated field) by Category and by Customer Segment allows direct comparison of risk levels. A highlight table is also appropriate here, but bar charts communicate magnitude more clearly to a leadership audience.

**Fields used:**
- Rows: Category (or Customer Segment — two separate views or one dual)
- Columns: Return Rate (calculated field: SUM([Return Flag]) / COUNT([Order ID]))
- Color: Red intensity based on return rate magnitude

**Design principle applied:** Sorted descending by return rate so the highest-risk categories are immediately visible at the top.

**Mistake avoided:** Did not show absolute return counts without normalizing — raw counts favor large-volume categories and would mislead the audience (e.g., Technology has more orders so more absolute returns, but a lower rate).
