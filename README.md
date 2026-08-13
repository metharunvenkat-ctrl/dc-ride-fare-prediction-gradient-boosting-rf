# 🚖 Washington DC Ride Fare Prediction & Spatial-Temporal Analytics

An end-to-end Machine Learning and Predictive Analytics solution designed to model urban mobility dynamics, analyze spatial-temporal pricing factors, and accurately forecast total ride fares in Washington DC using high-performance ensemble regression models (**Random Forest Regressor** & **Gradient Boosting Regressor**).

---

## 📌 Executive Summary

Accurate ride fare forecasting is fundamental for dynamic pricing engines, demand forecasting, fleet management, and consumer transparency in urban transportation ecosystems. This project delivers a production-grade data science pipeline that ingests real-world Washington DC taxi trip data, executes rigorous data quality enforcement (imputation and statistical outlier elimination), extracts spatial-temporal features, and trains predictive ensemble models to estimate total ride fares (`TOTALAMOUNT`).

---

## 📊 Benchmark Model Performance

Models were trained on an 80/20 train-test split and evaluated across standard regression metrics along with a domain-specific **±10% Fare Tolerance Accuracy** metric:

| Metric | 🌲 Random Forest Regressor | 🚀 Gradient Boosting Regressor |
| :--- | :---: | :---: |
| **Mean Absolute Error (MAE)** | **0.79** | 0.98 |
| **Root Mean Squared Error (RMSE)** | **1.37** | 1.42 |
| **R² Score (Variance Explained)** | **0.96** | **0.96** |
| **Prediction Accuracy (Within ±10% Tolerance)** | 89.28% | **90.18%** |

### Key Takeaways:
- **Gradient Boosting Regressor** achieved the highest overall operational accuracy, correctly predicting **90.18%** of test ride fares within a ±10% margin of error.
- **Random Forest Regressor** demonstrated superior overall error minimization with an MAE of **0.79** and an RMSE of **1.37**.

---

## 🏗️ End-to-End System Architecture

```
  ┌────────────────────────────────────────────────────────────────────────┐
  │ 📥 1. DATA INGESTION & QUALITY ENFORCEMENT                             │
  │  • Raw trip data parsing and schema validation                         │
  │  • Whitespace & non-numeric artifact stripping from location codes     │
  │  • Multi-variate missing data imputation via `KNNImputer`              │
  │  • Anomaly & extreme value filtering using Interquartile Range (IQR)    │
  └───────────────────────────────────┬────────────────────────────────────┘
                                      │
                                      ▼
  ┌────────────────────────────────────────────────────────────────────────┐
  │ ⚙️ 2. FEATURE ENGINEERING & SPATIAL-TEMPORAL ANALYSIS                  │
  │  • Temporal extraction: Pickup `hour_of_day`, `day_of_week`            │
  │  • Spatial categorization: `ORIGINCITY`, `DESTINATIONCITY`, ZIP codes  │
  │  • Core numerical signals: `MILEAGE`, `DURATION`, `FAREAMOUNT`,        │
  │    `GRATUITYAMOUNT`, `trip_duration`                                   │
  │  • Gratuity pattern analysis across payment modalities                 │
  └───────────────────────────────────┬────────────────────────────────────┘
                                      │
                                      ▼
  ┌────────────────────────────────────────────────────────────────────────┐
  │ 🤖 3. ENSEMBLE MODELING & PERFORMANCE BENCHMARKING                     │
  │  • 80/20 Train-Test Split with reproducible random states              │
  │  • Hyperparameter tuning (1,000 estimators per ensemble model)         │
  │  • Statistical validation: MAE, RMSE, R² Score, and ±10% Accuracy      │
  └────────────────────────────────────────────────────────────────────────┘
```

---

## 🔍 Business Insights & Key Findings

1. **Primary Fare Drivers**: Base fare (`FAREAMOUNT`), trip distance (`MILEAGE`), tip amount (`GRATUITYAMOUNT`), and total `trip_duration` were identified as the strongest predictive features.
2. **Temporal Fluctuations**: Demand and pricing exhibit distinct surge patterns during evening rush hours and weekend periods.
3. **Spatial Hotspots**: Key origin and destination hubs (airports, downtown commercial districts, transit hubs) command consistently higher average total fares.
4. **Payment Dynamics**: Electronic and credit card payment channels exhibit significantly higher gratuity rates compared to traditional cash transactions.

---

## 📂 Repository Structure

```
.
├── ride_fare_prediction.ipynb   # Primary Jupyter Notebook (Data Processing, EDA & ML Pipeline)
└── README.md                     # Production Documentation & Project Report
```

---

## 🛠️ Technical Stack & Tools

- **Programming Language**: Python 3
- **Data Engineering & Manipulation**: Pandas, NumPy
- **Machine Learning & Modeling**: Scikit-Learn (`RandomForestRegressor`, `GradientBoostingRegressor`, `KNNImputer`, `StandardScaler`)
- **Data Visualization**: Seaborn, Matplotlib

---

## 👤 Author & Project Ownership

**Tharun Venkat Sai Murugan**  
*Data Engineer / Data Scientist*  

*This repository represents an independent, end-to-end data science and machine learning solution demonstrating data quality engineering, spatial-temporal exploratory analysis, ensemble model benchmarking, and production-ready code design.*
