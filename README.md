# 🏠 Seattle House Sales: Market Intelligence Dashboard

## 📋 Project Overview

This [Tableau](https://public.tableau.com/views/HouseSalesdashboard_17018293652900/HouseSalesdashboard?:language=en-US&:display_count=n&:origin=viz_share_link)
project delivers a **comprehensive market intelligence analysis** of the King County / Seattle housing market.
Using a dataset of **21,000+ residential property sales**, I built an **interactive Tableau dashboard** that enables stakeholders to identify pricing trends, evaluate property characteristics, and make **data-driven real estate and investment decisions**.

The objective was to move beyond *“pretty charts”* and create a **decision-support tool** that answers critical business questions:

* How does **Property Grade vs. Condition** impact market value?
* What is the measurable **price premium for waterfront and scenic views**?
* Which **zip codes** offer the best **value-to-price ratio**?

---

## 🛠️ Technical Stack & Skills

**Tools & Platforms**

* **Tableau Desktop / Tableau Public**
* **Tableau Prep**
* **Excel / CSV**

**Data Source**

* King County House Sales Dataset

**Advanced Tableau Techniques**

* **LOD Expressions**

  ```text
  { FIXED [Zipcode] : AVG([Price]) }
  ```

  Used to create neighborhood-level pricing benchmarks.
* **Parameters**
  Enabled dynamic, user-driven filtering for budget exploration.
* **Dual-Axis Mapping**
  Combined sales density with price heatmaps for richer geospatial insights.
* **Calculated Fields**

  * Price per SqFt
  * Years Since Renovation

---

---

## 📖 Data Dictionary

To ensure full transparency in my analysis, here is a breakdown of the primary attributes found in the `Seattle_House_Sales.csv` dataset.

| Feature | Data Type | Description |
| --- | --- | --- |
| `id` | Numeric | Unique identifier for each house sale. |
| `date` | Date | Date the house was sold (Cleaned from raw string format). |
| `price` | Numeric | **Target Variable:** Sale price in USD. |
| `bedrooms` | Numeric | Number of bedrooms. |
| `bathrooms` | Numeric | Number of bathrooms (includes partial baths as .25, .5, or .75). |
| `sqft_living` | Numeric | Square footage of the interior living space. |
| `sqft_lot` | Numeric | Square footage of the land space. |
| `floors` | Numeric | Total floors (levels) in the house. |
| `waterfront` | Binary | Dummy variable; `1` if the property has a view to a waterfront, `0` otherwise. |
| `view` | Ordinal | An index from 0 to 4 of how good the view of the property was. |
| `condition` | Ordinal | An index from 1 to 5 on the condition of the apartment. |
| `grade` | Ordinal | An index from 1 to 13, where 1-3 falls short of construction and design, 7 is average, and 11-13 is high-quality construction. |
| `yr_built` | Date/Year | The year the house was initially built. |
| `yr_renovated` | Date/Year | The year of the house’s last renovation (0 if never renovated). |
| `zipcode` | Categorical | Five-digit code for the neighborhood location. |

---

## 🔄 Data Analysis Workflow

I followed a standard **CRISP-DM** (Cross-Industry Standard Process for Data Mining) approach to ensure the dashboard remained aligned with business objectives.

### 1. Requirements Gathering

I defined the three core personas for this dashboard: the **Budget Buyer**, the **Luxury Investor**, and the **Regional Agent**. Each requires different levels of granularity (e.g., Zipcode vs. Total Market Trends).

### 2. ETL (Extract, Transform, Load)

I used Tableau Prep to join spatial data with the sales records. This allowed me to create a seamless drill-down experience from the "City Level" to the "Street Level" without losing performance.

### 3. Iterative Design

I utilized "Dashboard Actions" to ensure that clicking on a specific bar in the `Price by Grade` chart would automatically filter the map to show where those specific high-grade homes are located.

---

## 📈 Key Formulas Used

To determine market efficiency, I calculated the **Price per Square Foot** () and used it as a normalized metric to compare different neighborhoods:

I also calculated the **Renovation Age** to see if "recent" updates had a diminishing return over time:

---


## 🔍 Data Analysis Process

### 1. Data Cleaning & Preparation

Before visualization, several data quality issues were addressed in **Tableau Prep**:

* **Outlier Management**
  Removed unrealistic records (e.g., homes with 33 bedrooms) to prevent skewed averages.
* **Feature Engineering**
  Created a binary `Is_Renovated` field to distinguish original builds from modernized properties.
* **Temporal Formatting**
  Converted string-based date fields into proper `Date` objects for time-series analysis.

---

### 2. Analytical Deep Dive

The core analysis focused on the relationship between **Property Grade (construction quality)** and **Sale Price**.

**Key Finding**

> While *Condition* (maintenance level) matters, **Property Grade shows a ~2.4× stronger correlation** with final sale price in the Seattle housing market.

This insight highlights that **build quality outweighs cosmetic condition** in long-term valuation.

---

### 3. Dashboard Features

* **Executive Summary**
  High-level view of daily average sales, volume, and price distributions.
* **Geospatial Analysis**
  Interactive map allowing drill-down by zip code and neighborhood.
* **Condition vs. View Matrix**
  Scatter plot revealing the *“investment sweet spot”*:

  * High condition
  * Lower price per square foot

---

## 💡 Key Business Insights

* **The View Premium**
  Homes with *Waterfront* or *Excellent View* ratings command an average **32% price premium**, independent of square footage.
* **Seasonal Volatility**
  Prices consistently peak in **Q2 (April–June)**.
  👉 Buyers seeking value should target **late Q4**.
* **The Renovation Gap**
  Homes renovated within the last **10 years** sold for **18% more** than similar properties last updated in the 1980s.

---

## 🚀 How to View the Project

* **Tableau Public Dashboard**
  👉 *![House Sales Visualization- Tableau](https://github.com/SteveJoe-cloud/Housing-Project-Tableau/assets/142490273/57d1a9eb-64e9-4db4-8dfc-90aefdb5f433)*
  
---

## 📁 Repository Structure

```text
/
├── Data/
│   └── king_county_house_sales.csv
├── Workbook/
│   └── seattle_housing_dashboard.twbx
└── README.md
```

