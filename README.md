# Wine Quality Classification with Cost-Sensitive Evaluation

## Project Overview

This project aims to classify wines into two categories based on their quality scores:

- High quality (Premium)
- Low quality (Normal)

The original dataset contains physicochemical properties of wines (such as acidity, sugar, alcohol, and pH) along with a quality score ranging from 0 to 10.

For this project, the target variable was transformed into a binary classification problem:

- High quality (1): wines with a score of 7 or higher  
- Low quality (0): wines with a score of 6 or lower  

This transformation allows the problem to be approached as a decision-making task rather than a regression problem.

---

## Business Objective

The goal is not only to classify wines correctly, but to **maximize business value** by accounting for the cost of different types of prediction errors.

A cost matrix is defined as follows:

- True Positive: +5  
- True Negative: +1  
- False Positive: -10  
- False Negative: 0  

This setup reflects a scenario where incorrectly labeling a low-quality wine as premium is significantly more costly than missing a high-quality wine.

---

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
6. Cost-sensitive evaluation using profit

---

## Results

Random Forest achieved the best overall performance from a business perspective, delivering the highest profit by effectively minimizing costly false positive predictions.

---

## Key Insight

The model with the best traditional metrics is not always the most valuable. Aligning model evaluation with business objectives is critical for real-world decision-making.

---

## Technologies

- Python
- Pandas, NumPy
- Scikit-learn
- XGBoost
- Matplotlib / Seaborn

