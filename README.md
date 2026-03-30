# Used Car Market Analysis

## Overview
This project is an interactive web application that visualizes key insights from a dataset of U.S. used car listings. By building a dashboard with **Streamlit** and **Plotly**, I created a tool that helps car buyers, sellers, and dealers quickly understand market trends – from price distributions and depreciation patterns to the dominance of various vehicle types. The app allows users to filter data interactively, making it easy to explore questions like “How does mileage affect price?” or “Which vehicle types hold their value best?”

## Business Problem
The used car market is large, fragmented, and driven by many factors – price, age, mileage, fuel type, and vehicle type. Sellers need to set competitive prices; buyers want to know what’s a fair deal; and dealers need to stock inventory that will sell. Without a centralized, interactive tool, these stakeholders rely on guesswork or time‑consuming manual research. This dashboard solves that by providing real‑time visual insights that help users make data‑driven decisions.

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
