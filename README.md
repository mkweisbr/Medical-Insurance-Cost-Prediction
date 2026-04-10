# Medical Insurance Cost Prediction using Regression Analysis

This project builds an Ordinary Least Squares (OLS) regression model to predict medical insurance charges based on demographic and health-related attributes.

The focus of this project is not only prediction, but also statistical interpretability through feature engineering, interaction terms, and multicollinearity analysis.

---

## Problem Statement

Medical insurance costs vary significantly across individuals based on factors such as age, BMI, smoking habits, and family structure.  
The goal of this project is to quantify these effects and build an interpretable model to predict insurance charges.

---

## Dataset Overview

The dataset includes the following features:

- `age`: Age of the individual  
- `sex`: Gender  
- `bmi`: Body Mass Index  
- `children`: Number of dependents  
- `smoker`: Smoking status  
- `region`: Residential region  
- `charges`: Medical insurance cost (target variable)

---

## Methodology

### 1. Data Preprocessing
- One-hot encoding applied to categorical variables using `get_dummies`
- Converted all variables to numeric format for regression analysis

### 2. Feature Engineering
To improve interpretability and model stability:
- Centered continuous variables:
  - `age_c`, `bmi_c`, `children_c`
- Created interaction terms:
  - `age_bmi`
  - `smoker_bmi`
  - `age_children`

### 3. Model Building
- Applied Ordinary Least Squares (OLS) regression using Statsmodels
- Included main effects and interaction terms

### 4. Multicollinearity Check
- Variance Inflation Factor (VIF) used to detect multicollinearity
- After centering variables, multicollinearity was significantly reduced:
  - Most VIF values ~ 1–1.6 (excellent stability)

### 5. Model Diagnostics
- Actual vs Predicted plot
- Residuals vs Fitted values plot
- Statistical summary of regression assumptions

---

## Model Performance

- **R-squared:** 0.841  
- **Adjusted R-squared:** 0.840  
- **F-statistic p-value:** < 0.001  

The model explains approximately **84% of the variance** in insurance charges, indicating strong predictive performance for real-world data.

---

## Key Findings

### Most Important Predictor
- Smoking status is the strongest driver of insurance costs:
  - **Smokers pay approximately +$23,840 more** than non-smokers on average.

---

### Other Key Effects
- Age increases insurance cost by approximately **+$263 per year**
- Each additional dependent increases cost by approximately **+$514**
- BMI alone is not statistically significant

---

### Interaction Effects
- `smoker_bmi` is highly significant, suggesting that:
  > The effect of BMI on insurance cost is much stronger for smokers.

This indicates a compounding risk effect between smoking and body mass.

---

### Regional Effects
- Southeast and Southwest regions show slightly lower charges compared to the baseline region
- Region is a weaker predictor compared to health and lifestyle factors

---

## Model Diagnostics Insights

- Residuals are not perfectly normally distributed (common in real-world insurance data)
  - Skewness: 2.53  
  - Kurtosis: 10.39  
- However, this does not significantly affect model interpretability or predictive usefulness

---

## Multicollinearity Analysis (VIF)

After applying feature centering:

| Feature | VIF |
|--------|-----|
| Most features | ~1.0 – 1.6 |
| Intercept | ~5.45 |

✔ This indicates **very low multicollinearity** and a stable regression model.

---

## Key Insight Summary

- Smoking is the dominant factor in predicting insurance costs
- Age and number of dependents have moderate effects
- BMI becomes important primarily when interacting with smoking status
- Feature centering significantly improved model stability and interpretability

---

## Tools Used

- Python
- Pandas
- NumPy
- Statsmodels
- Matplotlib
- Scikit-learn (preprocessing utilities)

---
