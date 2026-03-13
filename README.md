# YouTube Video Analysis — Casey Neistat's Channel

**MSc Business Analytics Dissertation | Aston University | 2023**  
**Author: Aravind Kalissery Vijayakumar**

---

## Overview

This project presents a comprehensive analysis of YouTube videos from **Casey Neistat's channel**, one of the most prominent individual creators on the platform. The goal was to identify the key variables that influence viewer engagement, and to build regression models capable of predicting an **Engagement Score** — a composite metric derived from views, likes, and comments.

Data was collected using the **YouTube Data API**, capturing video-level attributes including views, likes, comments, duration, publishing time, video category, and the presence of tags.

---

## Repository Structure

```
├── YouTube_Video_Analysis_Complete.ipynb   # Full pipeline — EDA, preprocessing, and all models
└── README.md
```

The notebook contains the complete end-to-end workflow in a single file: data loading, exploratory data analysis, outlier treatment, feature scaling, baseline, and all seven regression models with evaluation plots.

---

## Project Pipeline

### 1. Data Collection
- YouTube Data API v3
- Variables: Video ID, Views, Likes, Comments, Duration (seconds), Tag presence (Yes/No), Category, Published date and time

### 2. Exploratory Data Analysis (EDA)
- Correlation matrix and heatmaps
- Distribution plots and histograms of engagement metrics
- Boxplots by category and time of day
- Scatter plots across engagement variables
- Pivot tables and bar charts of average engagement by category
- Pairplot of numerical variables
- Frequency distributions for category, time of day, and tag variables

### 3. Outlier Treatment
- IQR-based outlier capping (factor = 1.5) applied to: Views, Likes, Comments, Duration, Engagement Score
- Boxplots before and after treatment to confirm effect

### 4. Feature Scaling & Train/Test Split
- 80/20 train/test split
- StandardScaler applied for distance and gradient-based models (MLR, KNN, Neural Network, GBR, XGB)
- Tree-based models (Decision Tree, Random Forest) trained on unscaled features

### 5. Baseline Model
- Predicts the mean Engagement Score for all observations
- MSE: `0.000669` | RMSE: `0.025870` | MAE: `0.020379`

### 6. Regression Models
Seven regression models were trained and evaluated. Each model section includes: performance metrics (MSE, RMSE, MAE for both train and test sets), actual vs predicted scatter plot(s), residual plot, and learning curve.

| Model | MSE (Test) | RMSE (Test) | MAE (Test) |
|---|---|---|---|
| Multiple Linear Regression | 1.26e-05 | 0.003553 | 0.002072 |
| Decision Tree Regression | 2.94e-05 | 0.005425 | 0.003462 |
| K-Nearest Neighbours (KNN) | 1.56e-04 | 0.012498 | 0.005293 |
| Random Forest Regression | 2.00e-05 | 0.004473 | 0.002850 |
| Gradient Boosting Regression | 1.49e-05 | 0.003865 | 0.002186 |
| Neural Network Regression | 1.46e-03 | 0.038207 | 0.023521 |
| **XGBRegressor** | **1.19e-05** | **0.003451** | **0.002008** |
| Baseline | 6.69e-04 | 0.025870 | 0.020379 |

---

## Key Findings

- **XGBRegressor** achieved the best overall performance with the lowest MSE, RMSE, and MAE on the test set.
- **Multiple Linear Regression** and **Gradient Boosting Regression** were close runners-up, both delivering strong predictive accuracy.
- **Random Forest** and **Decision Tree** delivered competitive results and are well-suited where model interpretability is a priority.
- **KNN Regression** underperformed relative to other models, likely due to its sensitivity in higher-dimensional feature spaces.
- **Neural Network Regression** recorded the highest error among all models, most likely due to the relatively small dataset size limiting its ability to generalise.
- All seven models significantly outperformed the baseline, confirming that the selected features are meaningful predictors of engagement.

---

## Requirements

```
pandas
numpy
matplotlib
seaborn
scikit-learn
xgboost
openpyxl
```

Install all dependencies with:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn xgboost openpyxl
```

> **Note:** The notebook loads data from a local Excel file. Update the file path in the data loading cell to point to your local copy of the dataset before running.

---

## Tools & Technologies

- **Language:** Python 3
- **Environment:** Jupyter Notebook
- **Data Source:** YouTube Data API v3
- **Key Libraries:** pandas, scikit-learn, XGBoost, matplotlib, seaborn

---

## Academic Context

This project was submitted as part of the **MSc Business Analytics** programme at **Aston University** (2023). It forms the analytical component of the dissertation exploring engagement dynamics on YouTube through machine learning.
