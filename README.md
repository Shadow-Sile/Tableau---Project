# -> Airbnb Data Analysis — Interactive Dashboard in Tableau

Project built as a data visualization practice by a 18-year-old student training as a **Data Analyst**. 
Using a real Airbnb listings dataset, an **interactive Tableau Public dashboard** was created to analyze prices, occupation rates, and estimated revenue by geographic area and property type.

---

## -> Dataset

The source file (`Tableau Full Project.xlsx`) contains two tables related through an `INNER JOIN` on `Listings.id = Calendar.listing_id`:

| Table | Records | Description |
|-------|---------|-------------|
| `Listings` | ~3,818 rows | Full details for each property listing |
| `Calendar` | ~10,000 rows | Daily availability and price per listing |

### Key columns used in the analysis

| Column | Table | Description |
|--------|-------|-------------|
| `price` | Listings | Nightly price of the listing |
| `bedrooms` | Listings | Number of bedrooms |
| `zipcode` | Listings | Location zip code |
| `accommodates` | Listings | Maximum number of guests |
| `availability_365` | Listings | Days available throughout the year |
| `room_type` | Listings | Type of room (Entire home, Private room…) |
| `date` | Calendar | Availability date |
| `available` | Calendar | Whether the listing is available on that day |

---

## -> Calculated Fields

Three **custom calculated fields** were created inside Tableau to derive relevant business metrics not directly available in the raw data:

### `Avg Revenue`
```
[price] * (365 - [availability_365])
```
Estimates the **annual revenue** of each listing by multiplying the nightly price by the number of occupied days (365 minus available days). To identify which property types generate the most income.

### `Tax Occupation %`
```
(365 - [availability_365]) / 365 * 100
```
Calculates the **annual occupation rate** of each listing — what percentage of the year it is actually registered. For comparing performance across different areas.

### `Price per Guest`
```
[price] / [accommodates]
```
Normalizes price by dividing it by the number of guests the listing has. Allows **compares between listings different sizes**, where a higher price can be reasonable if it sleeps more people.

---

## -> Visualizations — Worksheets

The project is made up of **11 individual worksheets** that feed into the final dashboard:

### KPI Cards (summary metrics)
Three single-number cards that provide immediate context to the viewer:

- **`Total Listings (card)`** — total number of listings analyzed in the dataset.
- **`Total Revenue (card)`** — total estimated revenue by summing `Avg Revenue` across all listings.
- **`Avg Price/Night (card)`** — average nightly price across the entire dataset.

### Geographic analysis by zip code
- **`Price By ZipCode`** — ranking of average prices by area to identify the most expensive neighborhoods.
- **`Price Per Zipcode`** — geographic map of price by zip code, showing the spatial distribution of pricing.
- **`Occupation Rate % by Zipcode`** — average occupation rate by area, useful for finding the most in-demand neighborhoods.

### Analysis by number of bedrooms
- **`Avg Price Per Bedrooms`** — how average price varies depending on the number of bedrooms.
- **`Distinct Count of Bedrooms Listings`** — supply distribution: how many listings exist for each size category.
- **`Total Revenue by Bedrooms`** — which bedroom segment generates the most total revenue.

### Cross analysis and time series
- **`Price vs Occupation Rate %`** — relationship between price and occupation rate. Reveals whether more expensive listings get booked less, or whether the market act equally.
  
- **`Revenue Per Year`** — estimated revenue trend over the year, for detecting seasonality patterns.

---

## -> Dashboard — `RESULT`

The final dashboard (`RESULT`) consolidates the most relevant visualizations into a single interactive view. Filters allow the user to segment data by area, property type, or number of bedrooms, updating all charts simultaneously.

The layout follows a logical analysis: starting from global KPIs, then we move into geographic and property-type dates, and finishing with the revenue time series.

🔗 **https://public.tableau.com/app/profile/dario.mititelu7577/viz/ProyectoAirbnb_17755717044030/RESULT?publish=yes**

x  

---

## -> Techniques Applied

- Multi-table connection and JOIN directly from Excel in Tableau
- Custom calculated fields to build business-relevant metrics
- KPI cards for executive-level summary
- Geographic maps with color-encoded metrics
- Bar charts, scatter plots, and time series
- Interactive dashboard with synchronized cross-sheet filters
- Data storytelling oriented layout design

---

## -> Technologies Used

- **Tableau Public**
- Dataset in **Excel (.xlsx)** format with two related sheets
- Published on **Tableau Public**

---
