# Project Overview
This project aims to predict 30-day hospital readmissions for diabetic patients using machine learning techniques. Leveraging the Diabetes 130-US Hospitals for Years 1999–2008 dataset from the UCI Machine Learning Repository, the research focuses on identifying high-risk patients to improve healthcare outcomes and reduce hospital costs. The study combines robust data preprocessing, exploratory data analysis (EDA), feature engineering, and advanced predictive modeling to address challenges like class imbalance and model overfitting.

# Objectives
1. Understand Factors Influencing Readmissions: Analyze patient demographics, clinical features, and healthcare interactions.
2. Develop Predictive Models: Build machine learning models to predict readmissions within 30 days ("<30").
3. Evaluate and Optimize Models: Compare baseline, advanced, and ensemble models to identify the most effective approach.

# Dataset
## Source: [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/296/diabetes+130-us+hospitals+for+years+1999-2008)
## Key Features:
  - 101,766 records from 130 US hospitals (1999–2008).
  - 50 attributes, including demographics (age, race, gender), clinical data (lab results, diagnoses), and healthcare utilization.
  - Target variable: Readmission Status ("<30", ">30", "NO").
## Challenges Addressed:
- Significant class imbalance:
  - "NO": 53.91%
  - ">30": 34.93%
  - "<30": 11.16%
- Missing data in categorical and numerical features.

# Methodology
1. Data Preprocessing
- Imputation:
  - Categorical: Missing values replaced with "Unknown".
  - Numerical: Missing values replaced with median values.
- Feature Selection: Derived variables like hospital_interaction (healthcare utilization intensity) and chronic_count (number of chronic conditions).
- Normalization: Applied Min-Max Scaling to numerical features.
- Class Imbalance Handling:
  - Used SMOTE (Synthetic Minority Oversampling Technique) to generate synthetic samples for the minority class.
2. Exploratory Data Analysis (EDA)
- Visualization:
  - Correlation matrix to identify relationships between features.
  - Boxplots to detect and handle outliers.
  - Distributions of numerical and categorical variables to highlight trends.
- Insights:
  - Emergency admissions strongly linked to readmissions.
  - Key predictors: number of inpatient visits, medications, and time spent in the hospital.
3. Modeling
- Baseline Models: Random Guesser, Majority Class Predictor, Naïve Bayes.
- Advanced Models: Logistic Regression, Random Forest, XGBoost.
- Ensemble Approaches: Weighted Voting Classifier (Logistic Regression, Random Forest, XGBoost).
4. Metrics for Evaluation
- Accuracy: Overall correctness of predictions.
- Precision: Fraction of true positives among predicted positives.
- Recall: Fraction of true positives among actual positives.
- F1-Score: Harmonic mean of Precision and Recall.
- AUC-ROC: Measures model’s ability to distinguish between classes across thresholds.

# Results
## Model Performance
Model	| Precision	| Recall | F1-Score	| AUC-ROC
--- | --- | --- | --- |---
Random Guesser	| 0.80	| 0.50	| 0.59	| 0.51
Majority Class Predictor | 0.79 |	0.89 |	0.84 |	N/A
Naïve Bayes	| 0.84	| 0.14	| 0.07	| 0.51
Logistic Regression |	0.83 |	0.66 |	0.72 |	0.63
Random Forest |	0.81	| 0.88	| 0.84 |	0.58
XGBoost	| 0.83	| 0.89	| 0.84	| 0.61
Random Forest w/ Hyperparameter Tuning	| 0.81	| 0.87	| 0.84 |	0.58
Stacking Classifier	| 0.82	| 0.87	| 0.84 |	0.58
Weighted Voting Classifier | 0.83 | 0.89 | 0.84 | 0.62

## Key Findings
1. Top Predictors:
- Number of inpatient visits, medications, and time spent in the hospital.
- Derived features like hospital_interaction and chronic_count proved useful.
2. Ensemble Strength: The Weighted Voting Classifier effectively balanced Precision and Recall, achieving the best overall performance.
  
3. Challenges:
- Class imbalance remains a significant issue despite SMOTE.
- Advanced models like XGBoost showed signs of overfitting, emphasizing the need for robust validation.

## Visualizations
1. Correlation Matrix: Highlights relationships between key features.
2. Precision-Recall Curve: Demonstrates trade-offs between Precision and Recall for Random Forest.
3. Feature Importance Plot: Top 15 predictors identified by the Random Forest model. Number of inpatient visits, hospital interactions, number of medications, number of lab procedures, and time spent in the hospital, were the most predictive indicators of readmission results.

# Future Work
- Incorporate temporal data (e.g., trends over multiple hospital visits).
- Explore deep learning models for improved feature extraction.
- Address biases in demographic features to ensure fairness.
- Expand the dataset with additional clinical variables and a higher proportion of "<30" readmission cases.

# References
- Diabetes 130-US Hospitals Dataset: UCI Machine Learning Repository.
- Strack, B., et al. "Impact of HbA1c Measurement on Hospital Readmission Rates." BioMed Research International, 2014.
