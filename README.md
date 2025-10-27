# Data201

# DATA 201 Project — Washington State Electric Vehicle Population

**Student:** Farah Makkawi  
**Course:** DATA 201 — Data Science Project  
**Dataset:** Washington State Department of Licensing (DOL) — Electric Vehicle Population Data  
**Source:** [data.wa.gov](https://data.wa.gov)  
**Metadata Updated:** October 18, 2025  

---

## 🔍 Introduction

This project analyzes the population of electric vehicles (EVs) registered in the state of Washington.  
The dataset includes information on **Battery Electric Vehicles (BEVs)** and **Plug-in Hybrid Electric Vehicles (PHEVs)** registered through the Department of Licensing. It contains more than **260,000 records** and multiple variables such as model year, make, model, electric range, base MSRP, and vehicle type.

The goal of this analysis is to explore EV adoption trends, identify the most popular manufacturers, and study how electric range and price vary among vehicle types.

---

## ❓ Research Questions

1. How has **EV adoption changed by model year**?  
2. Which **manufacturers (makes)** are most common in Washington State?  
3. How does the **electric range** differ between **BEVs** and **PHEVs**?  
4. Is there a relationship between **base MSRP** and **electric range**?  
5. What is the **median electric range** for registered EVs based on a 10% random sample, and what is its **bootstrap confidence interval**?

---

## ⚙️ Data Preparation & Wrangling

The data was cleaned and prepared using **Pandas** and **NumPy**:
- Converted column names to snake_case.  
- Removed duplicates.  
- Converted numeric variables (`model_year`, `electric_range`, `base_msrp`) to numeric types.  
- Removed invalid model years (<1990 or future years).  
- Derived simplified columns:
  - `make_clean` → standardized vehicle makes  
  - `ev_type` → identified as “BEV” or “PHEV”  

After cleaning, the dataset contained **264,628 rows and 19 columns**.

---

## 📊 Exploratory Data Analysis (EDA)

The dataset was visualized using **Matplotlib**.  
Key visualizations include:

1. **Histogram — Model Year Distribution**  
   - Shows strong EV adoption growth after 2015.

2. **Bar Chart — Top 10 EV Makes**  
   - Tesla, Nissan, Chevrolet, and Ford are the most common manufacturers.

3. **Boxplot — Electric Range by EV Type**  
   - BEVs have much higher and more variable ranges compared to PHEVs.

4. **Scatterplot — MSRP vs. Electric Range**  
   - A moderate positive relationship shows that vehicles with longer ranges tend to have higher prices.

---

## 🧮 Statistical Inference: Bootstrap of the Median

A **10% random sample** of the dataset (~26,000 records) was taken to simulate nonparametric inference for the **median electric range**.

Since many PHEVs report a 0-mile electric range, a filtered sample (only `electric_range > 0`) was analyzed.

| Statistic | Value |
|------------|--------|
| Sample size | 10,143 |
| Median electric range | **53 miles** |
| 95% Bootstrap Confidence Interval | [53.0, 53.0] |
| Bootstrap repetitions | 5,000 |

**Interpretation:**  
Most plug-in hybrid vehicles in Washington have an electric-only range around 53 miles. The narrow confidence interval reflects the heavy concentration of these models.

---

## ✅ Project Requirements Checklist

| Requirement | Completed |
|--------------|------------|
| 1. Dataset ≥1000 rows and ≥4 columns | ✅ |
| 2. Wrangling with Pandas/NumPy | ✅ |
| 3. Visualizations with Matplotlib | ✅ |
| 4. At least two plot types (used 4) | ✅ |
| 5. Nonparametric inference (bootstrap) | ✅ |
| 6. Random sample ≈10% of data | ✅ |
| 7. GitHub link submitted | ✅ |
| 8. Presentation prepared | ✅ |

---

## 💡 Conclusions

- **EV adoption** has increased rapidly since 2015.  
- **Tesla** dominates the EV market in Washington.  
- **BEVs** offer significantly higher ranges than **PHEVs**.  
- **Price and range** show a positive relationship — higher range often means higher cost.  
- The **median electric range** (53 miles) shows that most EVs are still short-range plug-in hybrids, but newer BEVs are extending these limits.

---

## 🧠 Future Work

- Include **time-series analysis** to predict future EV adoption trends.  
- Add **geographic mapping** by county or city.  
- Investigate **charging infrastructure** and how it affects EV adoption.

---




**Author:** Farah Makkawi  
**Date:** October 2025  
**License:** Public data from [data.wa.gov](https://data.wa.gov)
