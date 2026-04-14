# Wine Quality Classification with Cost-Sensitive Evaluation

## Project Overview

This project aims to classify wines into two categories:

- High quality (Premium)
- Low quality (Normal)

Instead of focusing only on traditional machine learning metrics, the evaluation is aligned with a business-driven cost structure, where different types of classification errors have different economic impacts.

## Business Objective

The goal is to maximize profit by optimizing model predictions under the following cost matrix:

- True Positive: +5  
- True Negative: +1  
- False Positive: -10  
- False Negative: 0  

This setup makes reducing false positives the top priority.

## Approach

The project follows a structured workflow:

1. Exploratory Data Analysis (EDA)
2. Data cleaning and feature engineering
3. Model training:
   - Logistic Regression (baseline)
   - Random Forest
   - XGBoost
4. Model evaluation:
   - Precision, Recall, F1-score
   - PR AUC and ROC AUC
5. Threshold optimization
6. Profit-based comparison

## Results

Random Forest achieved the best overall performance from a business perspective, delivering the highest profit by effectively minimizing costly false positives.

## Key Insight

The model with the best traditional metrics is not always the most valuable. Aligning model evaluation with business objectives is critical for real-world decision-making.

## Technologies

- Python
- Pandas, NumPy
- Scikit-learn
- XGBoost
- Matplotlib / Seaborn
