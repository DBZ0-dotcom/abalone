# 🐚 Abalone Age Prediction - Machine Learning Project

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue)](https://www.python.org/)
[![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-1.0%2B-orange)](https://scikit-learn.org/)
[![XGBoost](https://img.shields.io/badge/XGBoost-Latest-red)](https://xgboost.readthedocs.io/)
[![Status](https://img.shields.io/badge/Status-Complete-success)]()

A comprehensive machine learning project to predict the age of abalone based on physical measurements. This project explores data preprocessing, outlier handling, feature engineering, and the comparison of multiple regression algorithms.

## 📋 Table of Contents
- [About the Project](#about-the-project)
- [Dataset](#dataset)
- [Methodology & Preprocessing](#methodology--preprocessing)
- [Model Results](#model-results)
- [How to Run](#how-to-run)
- [Team](#team)

---

## 🎯 About the Project
The goal is to predict the number of rings on an abalone's shell, which is a direct indicator of its age (`Age = Rings + 1.5`). This is a classic **Regression** problem. Accurately predicting age helps in marine biology research and sustainable harvesting practices.

---

## 📊 Dataset
- **Source:** [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/abalone)
- **Instances:** 4,177
- **Features:** 8 (Sex, Length, Diameter, Height, Whole weight, Shucked weight, Viscera weight, Shell weight)
- **Target:** `Rings` (Integer)

---

## 🛠️ Methodology & Preprocessing
1. **Data Cleaning:** Checked for null values and duplicates (none found).
2. **Outlier Detection:** Used IQR method on numerical columns. Identified and removed 4 extreme outliers in the `Height` column (indices: 1257, 3996, 1417, 2051) to prevent model skewing.
3. **Encoding:** Applied One-Hot Encoding (`pd.get_dummies`) to the categorical `Sex` feature.
4. **Scaling:** Applied `StandardScaler` to normalize numerical features before training.
5. **Feature Engineering:** Experimented with `PolynomialFeatures` (degrees 1-4) to capture non-linear relationships.

---

## 🏆 Model Results
We trained and evaluated 5 different regression models. **XGBoost** and **Tuned Random Forest** emerged as the top performers.

| Model | MAE | MSE | RMSE | R² Score |
| :--- | :---: | :---: | :---: | :---: |
| Decision Tree | 1.6932 | 5.9486 | 2.4390 | 0.5036 |
| Linear Regression | 1.5841 | 4.9693 | 2.2292 | 0.5853 |
| Polynomial Regression (deg 2) | 1.5223 | 4.9282 | 2.2199 | 0.5887 |
| **Random Forest (Tuned)** | **1.5093** | 4.8279 | 2.1973 | **0.5971** |
| **XGBoost** 🥇 | **1.5097** | **4.8166** | **2.1947** | **0.5980** |

### 📈 Actual vs Predicted (XGBoost / Random Forest)
![Actual vs Predicted Scatter Plot](images/actual_vs_predicted.png)
*The model shows a strong linear correlation between actual and predicted rings, with minor variance at the extreme ends of the age spectrum.*

---

## 💻 How to Run
1. Clone the repository:
   ```bash
   git clone https://github.com/DBZ0-dotcom/abalone.git
   cd abalone