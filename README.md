# Adult-Census-Decision-Tree

## Overview 
This repository contains a comprehensive machine learning analysis of the Adult Census Income dataset, focusing on predicting individual income levels using demographic and socioeconomic factors. The project leverages the 1994 US Census data to develop predictive models that accurately classify individuals into two income categories: **above or below $50,000 per year**.

---

## Dataset Information
- **Source**: UCI Machine Learning Repository / Kaggle  
- **Origin**: 1994 US Census Database  
- **Size**: 48,842 samples  
- **Features**: 15 total features  
  - **Categorical**: 9 features  
  - **Numerical**: 6 features  
- **Target Variable**: Income (>50K or ≤50K annually)  
- **Data Quality**: Contains missing values and data inconsistencies  

---

## Dataset Features
| Feature          | Type       | Description |
|------------------|-----------|-------------|
| Age              | Numerical | Age of individual |
| Workclass        | Categorical | Employment type (Private, Gov, Self-employed, etc.) |
| Education        | Categorical | Education level |
| Marital Status   | Categorical | Marital status |
| Occupation       | Categorical | Job occupation |
| Relationship     | Categorical | Family relationship |
| Race             | Categorical | Racial background |
| Sex              | Categorical | Gender |
| Capital Gain     | Numerical | Capital gains |
| Capital Loss     | Numerical | Capital losses |
| Hours per Week   | Numerical | Working hours per week |
| Native Country   | Categorical | Country of origin |

---

## Data Quality Issues
- **Missing Values**: 4,262 missing entries (marked as `?`)  
- **Affected Columns**: `workclass`, `occupation`, `native-country`  
- **Data Inconsistency**: `Income` column contains typo with `.` character  
- **Symbol Issues**: Unusual `?` symbols requiring preprocessing  

---

## Methodology
###Data Preprocessing Pipeline

1. Missing Value Handling
  - Replaced '?' symbols with null values
  - Filled missing values with column mode (most frequent value)
  - Cleaned income column typos (removed '.' character)
2. Feature Engineering
  - **Categorical Encoding:** Applied LabelEncoder to categorical variables
  - **Data Normalization:** Standardized numerical features
  - **Feature Selection:** Analyzed feature importance and correlations
3. Train-Test Split
  - Stratified split to maintain class distribution
  - Standard 80-20 or 70-30 split ratio

---

## Model Implementation
### Decision Trees

- **Hyperparameter Tuning:** Grid search across 33 configurations
- Parameters Optimized:
    - **max_depth:** [None, 10, 20, 30]
    - **min_samples_leaf:** [1, 50, 100]
    - **min_samples_split:** [2, 100, 200]
    - **criterion:** ['gini', 'entropy']
    - **max_features:** [None, 'sqrt', 'log2']
 - Evaluation Metrics
  - Primary Metrics: Accuracy, F1-Score, Precision, Recall
  - Additional Analysis: Confusion matrices, feature importance

---

## Decision Trees Performance 

| Configuration             | Accuracy | F1-Score | Precision | Recall | Parameters |
|---------------------------|----------|----------|-----------|--------|------------|
| Best Configuration        | 84.88%   | 0.633    | 0.778     | 0.534  | `max_depth=None, min_samples_leaf=1, min_samples=2, criterion='gini', max_features = None` |
| Balanced Configuration    | 84.49%   | 0.604    | 0.765     | 0.500  | `max_depth=10, min_samples_leaf=50, min_samples=100, criterion='gini', max_features = 'log2'` |
| Alternative Configuration | 84.21%   | 0.611    | 0.739     | 0.522  | `max_depth=10, min_samples_leaf=100, min_samples=100, criterion='entropy' max_features = 'log2'` |


## Key Findings

- Decision Trees achieve strong baseline performance with 84.88% accuracy
- Feature engineering significantly impacts model performance
- Hyperparameter tuning provides measurable improvements
- Education level emerges as top predictor
- Age and hours-per-week show strong correlation with income

Contact

- Author: Adela Kushta
- Email: adelakushta05@gmail.com

