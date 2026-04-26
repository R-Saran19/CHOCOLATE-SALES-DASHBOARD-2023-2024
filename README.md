# CHOCOLATE-SALES-DASHBOARD-2023-2024
# Sales-analysis-dashboard
## Recommended Structure and Order
### 1.	Project Title / Headline
A concise, descriptive name for the dashboard.
Example: 
🍫 Chocolate Sales Dashboard 2023-2024
**An interactive 3-page Power BI analytics dashboard analyzing $14.22M in chocolate sales across 100 stores, 6 countries, and 37,109 customers over 2 years.**

### 2.	Data Source
More info on where the data comes from and how it’s structured
Example:
Source:  https://www.kaggle.com/

The dataset contains **557,679 transaction records** from a global chocolate retail chain  operating **100 stores** across **6 countries** (USA, UK, Canada, France, Australia, Germany),  capturing detailed sales data spanning two years (2023–2024). It includes store location,  sales channel type (Airport, Mall, Online, Retail), product details (200 items from 6 brands  across 5 categories), transaction date, quantity, unit price, discount, revenue, cost, and  profit metrics, along with customer demographics (37,109 unique customers with age, gender,  and loyalty status). This comprehensive dataset enables sales performance analysis, product  portfolio optimization, geographic market insights, customer segmentation, trend visualization,  and strategic business reporting in Power BI.


## 📊 Quick Overview

| Metric | Value |
|--------|-------|
| **Total Revenue** | $14.22M |
| **Total Profit** | $5.69M (40% margin) |
| **Total Orders** | 557,679 |
| **Unique Customers** | 37,109 |
| **Total Units Sold** | 1,673,720 |
| **YoY Revenue Growth** | 43.31% |
| **Data Period** | Jan 2023 - Dec 2024 |


## 🎯 Business Problem & Solution

### **The Challenge**
- 100 stores across 6 countries with no visibility into performance
- 200+ chocolate products with unclear revenue drivers
- 37K+ customers with unknown purchasing patterns
- No way to quickly identify top performers or trends

### **The Solution**
This 3-page Power BI dashboard enables:
- ✅ Real-time visibility into revenue, profit, and growth metrics
- ✅ Product performance analysis (top 10 products = 51% of revenue)
- ✅ Geographic insights (Australia dominates at $3.57M)
- ✅ Customer demographics (35-54 age group = 76% of revenue)
- ✅ Dynamic filtering by year across all pages

### **Business Impact**
- **Marketing**: Target 35-54 age demographic (highest ROI)
- **Inventory**: Focus on top 10 products (51% of revenue)
- **Expansion**: Scale to Australia (proven strong market)
- **Channel Optimization**: Airport stores ($4.25M) outperform retail ($2.71M)

---

## 📄 Dashboard Pages

### **PAGE 1: Executive Summary**
**Purpose:** C-level overview (2-minute read)

**Key Visuals:**
- **KPI Cards**: Revenue ($14.22M), Profit ($5.69M), Orders (557K), Customers (37K), Units (1.67M)
- **Revenue Achievement Gauge**: 114.64% of target (exceeding goals)
- **YoY Growth Card**: 43.31% revenue increase
- **Unit Economics Cards**: Avg profit/order ($10.20), Avg order value ($25.50), Avg margin (40.01%)
- **Dual-Axis Line Chart**: Profit & units trend (Jan 2023 - Dec 2024)
- **Monthly Revenue Line**: Detailed performance ($408K low → $802K high)

**Key Insights:**
- Revenue exceeds target by 14.64%
- Strong 43% YoY growth momentum
- Seasonal peak visible in Oct-Nov (plan inventory accordingly)
- Consistent 40% profit margins across portfolio

---

### **PAGE 2: Product Performance Analysis**
**Purpose:** Product mix & profitability deep-dive (5-minute read)

**Key Visuals:**
- **Top 10 Products Bar**: Ferrero Dark Chocolate leads ($146.19K)
- **Category Revenue Donut**: Dark (22.63%), White (20.94%), Truffle (20.03%), Milk (18.98%), Praline (17.42%)
- **Category Units Pie**: Dark (379K), White (351K), Truffle (336K) units
- **Profit Margin by Category**: All categories ~40% (consistent pricing)
- **Category Summary Table**: 5 categories, 200 products, 40.01% avg margin
- **Brand Revenue Column**: Ferrero $2.65M (18.6%), Cadbury $2.63M (18.4%)
- **Product Unit Sales**: Top 10 products 17.3K-16.8K units each

**Key Insights:**
- Top 10 products = 51% of revenue (focus investment here)
- All categories have identical 40% margins (no margin-squeezed categories)
- Ferrero & Cadbury = 37% of total sales (strong brand concentration)
- Volume doesn't always equal revenue (White has high units but lower revenue)

---

### **PAGE 3: Store & Customer Performance**
**Purpose:** Geographic & demographic analysis (5-minute read)

**Key Visuals:**
- **Top 10 Stores Bar**: Stores 47, 98, 72 tied at $146K
- **Revenue by Country Bar**: Australia $3.57M, Canada $2.55M, UK $2.27M, France $2.25M, USA $2.15M, Germany $1.43M
- **Revenue by City Column**: Toronto $2.6M, London $2.3M, Paris $2.3M
- **Store Type Pie**: Airport $4.25M (30%), Online $3.56M (25%), Mall $3.70M (26%), Retail $2.71M (19%)
- **Loyalty Members Card**: 18,669 active members (50.4% penetration)
- **YoY Customer Growth Card**: 36.74% increase
- **Revenue by Age Group**: 35-54 age group drives $10.8M (76% of revenue)

**Key Insights:**
- Australia is strategic market ($3.57M = 25% of revenue)
- Airport stores unexpectedly outperform ($4.25M per location)
- Retail underperforming vs potential ($2.71M needs investigation)
- 35-54 age group is revenue sweet spot (tailor marketing here)
- 50.4% loyalty penetration shows strong engagement

## 🛠️ Technical Stack

| Component | Tool | Details |
|---|---|---|
| **BI Platform** | Power BI Desktop | Latest version |
| **Data Source** | Excel (5 files) | Cleaned CSV import |
| **Data Cleaning** | Excel | Removed: nulls, duplicates, date mismatches |
| **Calculations** | DAX | 15 essential measures |
| **Relationships** | Star Schema | 4 fact-to-dimension joins |
| **Visuals** | Power BI Native | 25+ charts across 3 pages |
| **Interactivity** | Slicers & Navigation | Cross-page filtering |

---

## 📊 Data Model

```
Sales (Fact: 557,679 transactions)
├─ Products (Dimension: 200 items)
├─ Stores (Dimension: 100 locations)
├─ Customers (Dimension: 37,109 people)
├─ Calendar (Dimension: 730 days)
└─ Demographics (Age groups, Loyalty status)
```

**Relationships:** All one-to-many, single direction (best practice)

### **Data Cleaning**
- Removed order_date < join_date mismatches
- Removed future join_dates (2025-2026)
- Removed nulls from critical columns
- Removed duplicate order IDs
- **Result**: 557K validated transactions from 1M+ raw

---

### **DAX Measures (12 Essential)**
```dax
Total Revenue = SUM(Sales[revenue])
Total Profit = SUM(Sales[profit])
Total Orders = COUNTROWS(Sales)
Customer Count = DISTINCTCOUNT(Sales[customer_id])
Profit Margin % = [Total Profit] / [Total Revenue] * 100
Avg Order Value = [Total Revenue] / [Total Orders]
Revenue Target = 2500000
Revenue Achievement % = [Total Revenue] / [Revenue Target] * 100
LY Revenue = CALCULATE([Total Revenue], SAMEPERIODLASTYEAR(Calendar[date]))
YoY Revenue Growth % = ([Total Revenue] - [LY Revenue]) / [LY Revenue] * 100
YoY Customer Growth % = ([Customer Count] - [LY Customers]) / [LY Customers] * 100
```

### **Calculated Columns**
    Product_Grouping = Concatenated Brand + Product Name + Category + Weight
        Why: Original product names had duplicates; concatenation creates unique identifiers
        Example: "Ferrero | Dark Chocolate 50% | Dark | 100g"
    Age_Group = Bucketed customers into age ranges (18-24, 25-34, 35-44, 45-54, 55-64, 65+)
        Why: Enables demographic segmentation and easier visualization

### **Global Year Filter**

    Location: Filter pane (right side)
    Scope: All 3 pages
    Type: Dropdown (2023, 2024, or both)
    Benefit: Single source of truth; prevents conflicting filters across pages

---

### **🎨 Design Standards**
Color Scheme
  Element	            Color	              Purpose
Primary/Revenue	 #6B4423 (Brown)	Main data, emphasis
Profit/Success	 #28A745 (Green)	Positive metrics
Volume  	 #0C3B66 (Navy)	Orders, counts
Target/Highlight #D4A574 (Gold)	Targets, alerts
Text	         #333333 (Dark Gray)	Labels, readability
Background	 #F5F5F5 (Light Gray)	Page background

---

Date Format

    Format: DD/MM/YYYY (18/04/2026)
    Reason: Source data from Indian system; prevents locale errors when region is changed
    Note: Power BI set to India locale to maintain consistency

---

📈 Key Performance Indicators
Financial

    Revenue: $14.22M (tracked monthly, 43% YoY growth)
    Profit: $5.69M (40% margin consistency across portfolio)
    Profit per Order: $10.20 (unit economics)

Operational

    Total Orders: 557,679 (customer transaction volume)
    Units Sold: 1,673,720 (inventory/supply metric)
    Avg Order Value: $25.50 (customer economics)

Growth & Performance

    YoY Revenue Growth: 43.31% (momentum validation)
    YoY Customer Growth: 36.74% (acquisition rate)
    Revenue Target Achievement: 114.64% (exceeding goals)

Customer

    Unique Customers: 37,109 (market reach)
    Loyalty Members: 18,669 (50.4% penetration)
    Target Demographic: 35-54 age group (76% of revenue)

---

🔍 Known Limitations & Considerations
Date Format (DD/MM/YYYY)

    Current: DD/MM/YYYY format maintained to prevent locale errors
    Why: Source system is Indian; changing to US format causes Power Query errors
    Production Fix: Standardize to YYYY-MM-DD (ISO 8601) format in ETL layer
    Impact: Currently stable; would modernize for enterprise deployment

Calculated Columns

    Product_Grouping: Concatenated field ensures uniqueness but increases data size slightly
    Age_Group: Hardcoded ranges; would implement dynamic grouping if age distribution changes

---

🚀 Future Improvements (v2.0)

    RFM Segmentation: Identify high-value, at-risk, lost customers
    Predictive Forecasting: 6-month revenue forecast using time series
    Customer Churn Prediction: Identify customers likely to churn
    Mobile Optimization: Responsive design for tablets/phones
    Drill-Through Navigation: Click products → detailed product performance
    What-If Scenarios: Model business decisions (e.g., discount impact)

---

📊 Files Included

    Chocolate_Sales_Dashboard.pbix – Main Power BI file
    README.md – This documentation
    DATA_DICTIONARY.md – Field definitions
    Screenshots (JPG) – Preview images of all 3 pages

---

👤 About This Project

Built as a portfolio project to demonstrate:

    ✅ Power BI dashboard development (3 pages, 25+ visuals)
    ✅ Data modeling (star schema, proper relationships)
    ✅ DAX proficiency (YoY calculations, complex measures)
    ✅ Business acumen (metrics answer real questions)
    ✅ Design thinking (visual hierarchy, color, usability)

---

## 🚀 How to Use

1. Download `Chocolate_Sales_Dashboard.pbix`
2. Open in Power BI Desktop
3. Click navigation buttons to switch pages
4. Use slicers to filter by metrics
5. Hover for detailed tooltips
6. Refresh data monthly for latest insights

---

**Last Updated:** April 26, 2026
**Data Currency:** December 2024
**Dashboard Version:** 1.0


### .	Screenshots / Demos
Show what the dashboard looks like. - ![Alt text]()
Example: ![Dashboard Preview](https://github.com/R-Saran19/CHOCOLATE-SALES-DASHBOARD-2023-2024/blob/2c79750fccf97d2077b2c39d3ce45a997a3254a8/CHOCOLATE%20SALES%20DASHBOARD%20-%20Page%201%20-%20Executive%20Summary.jpg)
[](https://github.com/R-Saran19/CHOCOLATE-SALES-DASHBOARD-2023-2024/blob/2c79750fccf97d2077b2c39d3ce45a997a3254a8/CHOCOLATE%20SALES%20DASHBOARD%20-%20Page%202%20-%20Product%20Performance%20Analysis.jpg)
[](https://github.com/R-Saran19/CHOCOLATE-SALES-DASHBOARD-2023-2024/blob/2c79750fccf97d2077b2c39d3ce45a997a3254a8/CHOCOLATE%20SALES%20DASHBOARD%20-%20Page%203%20-%20Store%20%26%20Customer%20Performance%20Analysis.jpg)

