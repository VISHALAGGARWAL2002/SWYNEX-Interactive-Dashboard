# Car Sales Analytics Dashboard (Power BI)

An interactive, multi-page Power BI report that analyses car sales across brands, dealers, states, fuel types, customer ratings and financing. The report covers sales from 2019 to 2025 and is designed to help sales, dealer-network and product teams monitor performance and spot trends.

---

## Table of Contents

1. [Project Overview](#project-overview)
2. [Key Metrics](#key-metrics)
3. [Report Pages](#report-pages)
4. [Dataset](#dataset)
5. [Key Insights](#key-insights)
6. [Data Quality Notes](#data-quality-notes)
7. [Tools and Features Used](#tools-and-features-used)
8. [How to Use the Report](#how-to-use-the-report)
9. [Possible Improvements](#possible-improvements)

---

## Project Overview

The dashboard consolidates transactional car sales data into six focused pages. Each page answers a specific business question:

| Page | Business Question |
|------|-------------------|
| Executive Summary | How is the business performing overall? |
| Sales Trend | How do revenue and volume change over months, quarters and years? |
| Product Mix | Which brands, models, colors, transmissions and fuel types sell best? |
| Dealer Scoreboard | Which dealers perform best on volume, price and revenue? |
| Geography | How does performance differ across states? |
| Customer & Finance | How satisfied are customers, and how are purchases financed? |

Most pages include slicers (for example Dealers, States, Year and Finance) so that every visual can be filtered interactively.

---

## Key Metrics

Headline figures shown on the Executive Summary page:

| Metric | Value |
|--------|-------|
| Total SaleID (number of sales) | 9,795 |
| Total Revenue | 18.22 bn |
| Average Car Price | 1.86 M |
| Average Customer Rating | 3.54 |
| Cars Sold | 9,795 |

---

## Report Pages

### 1. Executive Summary
- KPI cards: Total SaleID, Total Revenue, Avg. Car Price, Avg. Rating, Cars Sold
- Revenue by Brand (column chart)
- Revenue Share by Fuel Type (pie chart)
- Brand Revenue Share (pie chart)
- Yearly Revenue Trend (area chart, 2019 to 2025)
- Slicers: Dealers, States

### 2. Sales Trend
- Monthly Revenue by Year (multi-line chart)
- Month by Year revenue matrix with totals
- Cars Sold by Quarter (stacked column chart, split by year)
- Monthly Revenue Trend (area chart)
- Avg. Car Price by Year (line chart)

### 3. Product Mix
- Revenue by Brand and Model (treemap)
- Cars Sold by Color (donut chart)
- Cars Sold by Transmission (column chart)
- Fuel Type Mix by Brand (stacked column chart)

### 4. Dealer Scoreboard
- Dealer Performance: Cars Sold vs Avg. Price (scatter plot)
- Top 5 Dealers by Revenue (bar chart)
- Avg. Price by Dealer (bar chart)
- Dealer summary table: Sum of Price, Cars Sold, Average of Price
- Slicer: Dealers

### 5. Geography
- Revenue by State (filled map)
- Top 5 Brands by Revenue (ribbon chart)
- State summary table: Cars Sold, Sum of Price, Average of Price, Average Customer Rating
- State by Fuel Type matrix (CNG, Diesel, Electric, Hybrid, Petrol, not provided)
- Slicer: States
- A note on the page explains that records with state "not provided" are excluded from the map

### 6. Customer & Finance
- Avg. Customer Rating by Brand (bar chart)
- Cars Sold by Finance Status (pie chart)
- Price vs Customer Rating by Brand (scatter plot)
- Avg. Customer Rating by Dealer (bar chart)
- Company Name by Finance Status matrix (No, not provided, Yes)
- Slicers: Year, Finance

---

## Dataset

The report is built on a single table named `data`. The fields used in the model are:

| Field | Description |
|-------|-------------|
| SaleID | Unique identifier of each sale |
| SaleDate | Date of sale (with date hierarchy for year, quarter and month) |
| Year | Year of sale |
| Company Name | Car brand / manufacturer |
| Model | Car model |
| Color | Car color |
| FuelType | Petrol, Diesel, CNG, Electric, Hybrid |
| Transmission | Automatic, Manual, CVT |
| Mileage_km | Mileage of the vehicle in kilometers |
| Price | Sale price |
| Dealer | Dealer that made the sale |
| State | State where the sale took place |
| Finance | Whether the purchase was financed (Yes / No) |
| Customer_rating | Customer rating of the purchase |
| VIN | Vehicle identification number |
| Notes | Additional remarks |
| Car sold | Calculated measure: count of cars sold |

The data table also contains customer name and email columns. These are personal data and are not used in any visual. If this report is shared outside the team, consider removing or masking these columns.

---

## Key Insights

These observations are taken directly from the visuals in the report:

- **Revenue and volume:** The business recorded 9,795 sales and about 18.22 bn in revenue, at an average price of roughly 1.86 M per car.
- **Brand leadership:** Audi leads in revenue, followed by Mercedes-Benz and BMW. The top five brands by revenue are Audi, Mercedes-Benz, BMW, Ford and Volkswagen.
- **Fuel type:** Revenue is spread fairly evenly across fuel types, with no single fuel type dominating. Petrol, diesel, CNG, hybrid and electric all hold meaningful shares.
- **Transmission:** Automatic is the most common transmission, followed by Manual. A notable number of records have the transmission "not provided".
- **Dealers:** All ten dealers are closely matched, selling between 956 and 996 cars each. Metro Automobiles sold the most cars (996), Prestige Auto has the highest average price (about 1.90 M), and Capital Motors has the lowest average price (about 1.83 M).
- **Geography:** Delhi has the highest number of sales among named states (1,575), followed by Uttar Pradesh (1,573), Gujarat (1,043), Tamil Nadu (1,005) and Karnataka (997).
- **Financing:** Financed (Yes) and non-financed (No) purchases are almost equal, at 4,186 and 4,180 sales respectively.
- **Customer satisfaction:** The overall average rating is 3.54. Ratings across brands, dealers and states stay in a narrow band, between roughly 3.4 and 3.6.
- **Yearly trend:** Revenue peaked around 2020 and then declined gradually, with a sharp drop in 2025.

---

## Data Quality Notes

- **Missing values:** Several fields contain the value "not provided": State (1,594 records, about 16%), Finance (1,429 records), Transmission and FuelType. These are shown as their own category in most visuals.
- **Geography page:** Records with state "not provided" are excluded from the map, so the map does not represent the full 9,795 sales.
- **2025 data:** The sharp drop in 2025 revenue and in the later months of the Monthly Revenue by Year chart suggests that data for 2025 is incomplete or partial. Year-over-year comparisons that include 2025 should be interpreted with caution.
- **Customer information:** Customer name and email fields exist in the source table and should be handled according to your organization's data privacy policy.

---

## Tools and Features Used

- Microsoft Power BI Desktop
- Data model with a single fact table (`data`) and a date hierarchy on `SaleDate`
- DAX measure for `Car sold`
- Visuals: cards, column and bar charts, stacked charts, line and area charts, pie and donut charts, treemap, scatter plot, ribbon chart, filled map, matrix and table
- Slicers for Dealers, States, Year and Finance
- Dark theme with a consistent blue accent color
- Page navigation through report tabs

---

## How to Use the Report

1. Open the `.pbix` file in Power BI Desktop (or open the published report in the Power BI Service).
2. Start with the **Executive Summary** page for the high-level picture.
3. Use the page tabs at the bottom to move between Sales Trend, Product Mix, Dealer Scoreboard, Geography and Customer & Finance.
4. Use the slicers (Dealers, States, Year, Finance) to filter the visuals on a page. Click a checkbox to apply a filter and click it again to clear it.
5. Click on any bar, slice or data point to cross-filter the other visuals on the same page.
6. Hover over any visual to see tooltips with exact values.
7. To refresh the data, choose **Refresh** on the Home ribbon after updating the source file.

---

## Possible Improvements

- Add year-over-year and month-over-month growth measures.
- Add a Year slicer to the Executive Summary and Sales Trend pages.
- Standardize or impute the "not provided" values at the source to improve geographic and fuel type analysis.
- Add drill-through from brand to model to individual sales.
- Add profit or margin data to move from revenue analysis to profitability analysis.
- Add a data refresh schedule when the report is published to the Power BI Service.
- Mask or remove personal customer fields before wider distribution.
