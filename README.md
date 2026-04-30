## Wine Quality Classification with Cost-Sensitive Evaluation
A machine learning project that predicts wine quality using a business-oriented, cost-sensitive framework — where model selection and threshold optimization are driven by profit rather than statistical metrics alone.

#### Note: This is a simulated business case designed to reflect real-world decision-making scenarios.

### Problem Statement
A growing winery needs to classify wines as premium or standard without relying on expert evaluators. The challenge is not just predicting quality correctly, but avoiding a specific type of error: labeling a standard wine as premium. This mistake carries significant business consequences — customer dissatisfaction, batch returns, and reputational damage in new markets.
This project addresses the problem through a cost-sensitive classification approach, where each type of prediction error is assigned a monetary value and models are evaluated based on their total profit rather than statistical metrics alone.

### Notebooks
#### - 01_eda_processing.ipynb
Covers the full exploratory and preparation phase. This includes an analysis of the target variable distribution and class imbalance, correlation analysis between physicochemical features, outlier identification and treatment using targeted filtering, logarithmic transformation of skewed variables, feature engineering of the alcohol/density ratio, and binary encoding of the target variable.

#### - 02_modelling.ipynb
Covers the full modeling and evaluation phase. Three classification models are trained and evaluated — Logistic Regression, Random Forest, and XGBoost — all optimized around precision using GridSearchCV with Stratified K-Fold cross-validation. Each model is first assessed at the default threshold and then systematically optimized using a profit vs threshold framework derived from a predefined cost matrix. Final model selection is based on business profit rather than predictive metrics alone. The notebook also includes feature importance analysis for the selected model.

### Data
#### - wine_quality.csv 
Original dataset sourced from an academic institution, containing physicochemical measurements of wine samples with quality scores assigned by expert tasters.
#### - wine_clean_data.csv
Processed version of the dataset, output of 01_eda_processing.ipynb, ready for modeling.

### Tools & Libraries
Python · Pandas · NumPy · Scikit-learn · XGBoost · Matplotlib · Seaborn
