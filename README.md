# 🚖 Washington DC Ride Fare Prediction & Spatial-Temporal Analysis

An end-to-end Machine Learning and Data Science project analyzing urban mobility patterns and predicting ride fares in Washington DC using **Random Forest Regressor** and **Gradient Boosting Regressor** models.

---

## 📌 Project Overview

Accurate ride fare estimation is vital for ride-hailing platforms, transit planners, and passengers. This project analyzes real-world Washington DC taxi trip data, cleans corrupted and missing values, performs exploratory spatial and temporal data analysis, engineers key trip features, and builds high-precision machine learning regression models to predict total trip fare (`TOTALAMOUNT`).

---

## 📊 Key Machine Learning Model Results

Two advanced ensemble regression algorithms were trained and evaluated on test trip data:

| Metric | 🌲 Random Forest Regressor | 🚀 Gradient Boosting Regressor |
| :--- | :---: | :---: |
| **Mean Absolute Error (MAE)** | **$0.79** | $0.98 |
| **Root Mean Squared Error (RMSE)** | **$1.37** | $1.42 |
| **$R^2$ Score (Variance Explained)** | **0.96** | **0.96** |
| **Custom Accuracy (Within ±10% Fare)** | 89.28% | **90.18%** |

- **Gradient Boosting Regressor** achieved the highest overall accuracy within a 10% fare tolerance (**90.18%**).
- **Random Forest Regressor** yielded lower error metrics (MAE: **$0.79**, RMSE: **$1.37**).

---

## 🛠️ Data Pipeline & Methodology

```
  ┌───────────────────────────┐
  │  Raw Taxi Trip Data (CSV) │
  └─────────────┬─────────────┘
                │
                ▼
  ┌────────────────────────────────────────────────────────────────────────┐
  │  1. Data Cleaning & Preprocessing                                      │
  │  • Whitespace & special character removal across ZIP codes & cities   │
  │  • Removal of invalid/corrupt fields & ZIP length validation           │
  │  • Missing value imputation using `KNNImputer`                         │
  │  • Outlier filtering using Interquartile Range (IQR)                   │
  └─────────────┬──────────────────────────────────────────────────────────┘
                │
                ▼
  ┌────────────────────────────────────────────────────────────────────────┐
  │  2. Feature Engineering & Exploratory Data Analysis (EDA)              │
  │  • Extracted temporal features: `hour_of_day`, `day_of_week`           │
  │  • Extracted spatial features: `ORIGINCITY`, `DESTINATIONCITY`          │
  │  • Key numerical features: `MILEAGE`, `DURATION`, `FAREAMOUNT`,       │
  │    `GRATUITYAMOUNT`, `trip_duration`                                   │
  │  • Analyzed payment type distribution (Credit vs Cash vs EHail)        │
  └─────────────┬──────────────────────────────────────────────────────────┘
                │
                ▼
  ┌────────────────────────────────────────────────────────────────────────┐
  │  3. Model Training & Evaluation                                        │
  │  • Train/Test Split (80/20 ratio)                                      │
  │  • Hyperparameter tuned Ensemble Regressors (1000 estimators)          │
  │  • Performance evaluation: MAE, RMSE, R² Score, & ±10% Accuracy        │
  └────────────────────────────────────────────────────────────────────────┘
```

---

## 🔍 Key Research Questions Addressed

1. **What are the primary drivers of total ride fare?**
   - Base fare (`FAREAMOUNT`), trip distance (`MILEAGE`), tip amount (`GRATUITYAMOUNT`), and total `trip_duration` demonstrate the strongest correlation with `TOTALAMOUNT`.
2. **How do ride fares fluctuate spatially and temporally?**
   - Distinct fare spikes occur during evening peak hours and weekends.
   - High-demand origin/destination clusters (airports and central business districts) exhibit significantly higher average fares.
3. **What is the impact of payment methods on gratuity?**
   - Digital and credit card payments correlate with higher tip percentages compared to cash transactions.

---

## 📂 Project Repository Structure

```
.
├── DS_Proj_ride.ipynb       # Primary Jupyter Notebook (Data Cleaning, EDA & ML Pipeline)
├── Team18_Project_PPT.pptx  # Project Presentation & Technical Summary Slides
├── .gitattributes          # GitHub Linguist language override (Classifies notebook as Python)
├── .gitignore              # Excluded dataset CSV files, checkpoints, and temporary caches
└── README.md               # Comprehensive Project Documentation & Results
```

---

## 🚀 Technical Stack

- **Language**: Python 3
- **Data Manipulation**: Pandas, NumPy
- **Machine Learning**: Scikit-Learn (`RandomForestRegressor`, `GradientBoostingRegressor`, `KNNImputer`, `StandardScaler`)
- **Data Visualization**: Seaborn, Matplotlib

---

## 👤 Authors & Acknowledgments

- **Harish Base**
- **Tharun Venkat Sai Murugan**

Developed for Washington DC Ride Fare Prediction & Urban Mobility Pattern Analysis.
