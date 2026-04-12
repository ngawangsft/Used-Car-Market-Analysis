# Used Car Market Analysis

## Overview
This project is an interactive web application that visualizes key insights from a dataset of U.S. used car listings. By building a dashboard with **Streamlit** and **Plotly**, I created a tool that helps car buyers, sellers, and dealers quickly understand market trends – from price distributions and depreciation patterns to the dominance of various vehicle types. The app allows users to filter data interactively, making it easy to explore questions like “How does mileage affect price?” or “Which vehicle types hold their value best?”

## Business Problem
The used car market is huge, fragmented, and driven by many factors – price, age, mileage, fuel type, and vehicle type. Sellers need to set competitive prices; buyers want to know what’s a fair deal; and dealers need to stock inventory that will sell. Without a centralized, interactive tool, these stakeholders rely on guesswork or time‑consuming manual research. This dashboard solves that by providing real‑time visual insights that help users make data‑driven decisions.

## Key Insights & Highlights
The dashboard presents five main visualizations, each answering a core business question: 

| Question | Key Finding |
|----------|-------------|
| **How are used cars priced?** | Most used cars are priced between $3,000 and $10,000; the distribution is right‑skewed, with a long tail of luxury/rare vehicles above $40,000. |
| **How does mileage affect price across fuel types?** | Gasoline vehicles depreciate fastest with mileage; diesel vehicles retain value better; hybrid and electric cars are still rare in the dataset. |
| **Which vehicle types hold their value better?** | Off‑road vehicles and pickups show the strongest price‑age relationship (R² = 0.61 and 0.56), meaning their value depreciation is most predictable. Convertibles and “other” types have the weakest relationship (R² ≈ 0.15). |
| **R² value by vehicle type** | A dedicated bar chart quantifies how well age explains price variation for each vehicle type, highlighting the most predictable segments. |
| **What kinds of cars dominate listings?** | SUVs, sedans, and trucks together make up over 70% of listings; pickups, coupes, and wagons account for most of the remainder. |

## Tools & Technologies
- **Python** – data manipulation and analysis  
- **pandas** – cleaning and preparing the dataset  
- **Streamlit** – building the interactive web dashboard  
- **Plotly Express & Graph Objects** – creating interactive charts  
- **Seaborn / Matplotlib** – used for static exploration in the notebook  
- **Render** – hosting the deployed application  

## Dataset
The data comes from a public CSV file of used car advertisements (originally from a Kaggle dataset). It includes fields such as price, model year, odometer, fuel type, transmission, and vehicle type. The file is named `vehicles.csv` and is placed in the root of the project.

## How to Run the Project Locally
1. **Clone the repository**  
   ```bash
   git clone https://github.com/ngawangsft/Used-Car-Market-Analysis.git
   cd used-car-market-analysis


# Used Car Market Analysis

## Overview
This project analyzes a large dataset of U.S. used car listings to uncover market trends, pricing patterns, depreciation behavior, and brand value. I built two interactive tools:
- A **Streamlit + Plotly web app** for real‑time exploration
- A **Tableau Public dashboard** with deeper KPIs, price‑per‑mile analysis, and depreciation by make

Both tools help car buyers, sellers, and dealers make data‑driven decisions.

**Live Tableau Dashboard:** [View on Tableau Public](https://public.tableau.com/app/profile/rin.whyco/viz/WhatsontheRoadWhatsaDeal/Dashboard3)

---

## Business Problem
The used car market is huge, fragmented, and driven by many factors – price, age, mileage, fuel type, vehicle type, and brand. Sellers need to set competitive prices; buyers want fair deals; dealers need to stock inventory that sells. Without a centralized, interactive tool, stakeholders rely on guesswork or manual research. This project solves that by providing real‑time visual insights.

---

## Key Insights & Highlights (Streamlit App)
| Question | Key Finding |
|----------|-------------|
| **How are used cars priced?** | Most are priced between $3,000 and $10,000; the distribution is right‑skewed, with a long tail of luxury/rare vehicles above $40,000. |
| **How does mileage affect price across fuel types?** | Gasoline vehicles depreciate fastest; diesel retains value better; hybrid/electric are still rare. |
| **Which vehicle types hold value better?** | Off‑road vehicles and pickups show the strongest price‑age relationship (R² ≈ 0.61 and 0.56). Convertibles and “other” have the weakest (R² ≈ 0.15). |
| **R² by vehicle type** | A dedicated bar chart quantifies how well age explains price variation for each type. |
| **What kinds of cars dominate listings?** | SUVs, sedans, and trucks together make up over 70% of listings; pickups, coupes, wagons account for most of the remainder. |

---

## Tableau Dashboard: Advanced Market Analysis
I built an interactive **Tableau dashboard** that adds new layers of analysis:

- **KPIs** – Total listings, average price, average odometer, average days listed  
- **Market share by vehicle type** – Dominance of SUVs, sedans, trucks, pickups  
- **Brand value (price per mile)** – Bar chart comparing $/mile for each make, flagged above/below market average ($0.1155/mile).  
  - *Best value:* Acura ($0.052), Honda ($0.070), Hyundai ($0.075)  
  - *Above average:* Ram ($0.177), Mercedes‑Benz ($0.358), GMC ($0.137)  
- **Depreciation by brand** – Scatter plot (price vs. odometer) with trend lines per make. R² values show how strongly mileage predicts price:  
  - Volkswagen (R² ≈ 0.66) – most predictable  
  - Honda (R² ≈ 0.43) – balanced  
  - Acura (R² ≈ 0.24) – least predictable (trim/condition matter more)  
- **Global filters** – Adjust price ($1k–40k), odometer (10k–200k miles), model year (2000–2019), and make to explore subsets dynamically.

---

## Tools & Technologies
- **Python / pandas** – data cleaning, feature engineering, outlier removal  
- **Streamlit + Plotly** – interactive web dashboard  
- **Tableau Public** – supplementary dashboard for KPIs, price per mile, depreciation by brand  
- **Seaborn / Matplotlib** – static exploratory analysis  
- **Render** – hosting the Streamlit app  

---

## Dataset & Data Cleaning
The raw data comes from a public Kaggle CSV of used car ads (fields: price, model year, model, condition, fuel, odometer, transmission, type, paint color, is_4wd, date posted, etc.).

### Cleaning & Feature Engineering
I performed extensive cleaning and created new columns to enable meaningful analysis:

- **Imputed missing `is_4wd`** using model‑grouped means; if ≥85% of a model’s known values were 4WD, inferred 4WD for missing entries.
- **Filled missing `model_year`** with median per model and `is_4wd`, then rounded to integer.
- **Filled `cylinders`** using mode per model, falling back to overall mode.
- **Imputed `odometer`** with median grouped by `model_year` and `condition`, then by `model_year` alone, then overall median.
- **Filled `paint_color`** using mode per model.
- **Parsed `date_posted`** to datetime.
- **Removed outliers**:  
  - Price < $500  
  - Odometer > 200,000 miles  
  - Model year < 1980  
  - Suspicious combinations: price > $60k with mileage > 75k miles, price < $2k with mileage < 50k miles, placeholder prices (12345, 123456)  
- **Derived new columns**:  
  - `make` – extracted from model name using a mapping function  
  - `clean_model` – standardised model names (lowercase, stripped spaces, special fixes)  
  - `trim` – extracted trim level from the remaining part of the original model string  
- **Calculated `price_per_mile`** = price / odometer  
- **Flagged “above average”** (expensive) vs. “good value” based on market average price per mile  

Final cleaned dataset: **~42,000 used car listings** (after filtering out “new” condition).

---

## How to Run the Streamlit App Locally
1. **Clone the repository**  
   ```bash
   git clone https://github.com/ngawangsft/Used-Car-Market-Analysis.git
   cd used-car-market-analysis