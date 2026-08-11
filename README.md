# Metropolitan REIT — Housing Portfolio Analysis & ETL Pipeline

An end-to-end data analysis, anomaly auditing, and feature engineering for an institutional Real Estate Investment Trust (REIT). This project transforms messy raw housing transaction logs into an executive-ready staged dataset and BI dashboard wireframe.

---

## Business Problem & Context
The client manages a **$6.11B residential property portfolio** across multiple metropolitan regions. Prior to ingestion into executive dashboards, the raw data suffered from data quality issues, missing values, human input errors, and unsegmented property attributes.

**Core Objectives:**
1. Clean and audit 10,000+ raw property transaction records.
2. Automate anomaly detection for listing price errors and bedroom/sqft data typos.
3. Engineer business categorical attributes (Size Tiers, Age Categories) for BI dashboarding.
4. Uncover core market value drivers (e.g., Waterfront valuation premium & Renovation ROI).

---

## Key Business Findings & Strategic Insights

* **The Waterfront Multiplier:** Waterfront assets represent the single largest margin driver. In *Coastal Suburbs*, waterfront properties command an average price of **$2.24M** vs **$532K** for non-waterfront units—a **321% valuation markup**.
* **Renovation Value Uplift:** Renovated properties average **$602,313** vs **$489,337** for unrenovated assets, yielding a net value lift of **~$113,000 per renovated property**.
* **Regional Market Unit Valuation:** *Greenwood Valley* achieved the highest unit valuation efficiency at **$235.59/sq ft**, while *Coastal Suburbs* generated the highest total revenue (**$1.52B**).

---

## Engineering Workflow

### 1. Data Auditing & Automated Anomaly Detection
* **Price Corrections:** Handled `$0` and negative price anomalies using absolute transformations (`.abs()`) and dynamic mean replacement for zero-value entries.
* **Typo Detection Logic:** Implemented an automated condition rule to flag human entry errors on single-family properties:

### 2. Feature Engineering
* **Property Size Tier:** Created categorical bins (`Small` <1.5k sqft, `Medium` 1.5k–3k sqft, `Large` >3k sqft).
* **Property Age Group:** Calculated property age relative to operational year 2026 and binned properties into `New Construction`, `Modern`, and `Established`.

---

## Visualizations & Visual Architecture

### Market Performance Plots
The repository includes automated Python scripts (`seaborn` / `matplotlib`) generating:
1. **Waterfront vs. Non-Waterfront Price Comparison** across target cities.
2. **Price per SqFt Boxplots** highlighting regional variance and upper luxury outliers (>99th percentile cutoff at **$4.73M**).

### Executive Dashboard Wireframe (2x2 Grid)
Designed for seamless deployment to Tableau or Power BI:
* **Header KPI Cards:** Total Revenue ($6.11B) | Total Listings (10,250) | Avg Price/SqFt ($234.65) | Luxury Penetration (1.00%)
* **Top-Left:** Dual-Axis Combo Chart (Sales Volume vs. Gross Revenue by City)
* **Top-Right:** Side-by-Side Grouped Bar Chart (Waterfront Valuation Premium)
* **Bottom-Left:** Categorical Heatmap (Inventory Distribution by Size Tier & Age Group)
* **Bottom-Right:** Top 3 / Bottom 3 Zip Code Leaderboard Table

---
