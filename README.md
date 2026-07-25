#  House Prices Prediction using Ensemble Machine Learning

<p align="center">

![Python](https://img.shields.io/badge/Python-3.11-blue?style=for-the-badge&logo=python)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-ML-orange?style=for-the-badge&logo=scikitlearn)
![XGBoost](https://img.shields.io/badge/XGBoost-Ensemble-success?style=for-the-badge)
![LightGBM](https://img.shields.io/badge/LightGBM-Gradient%20Boosting-green?style=for-the-badge)
![CatBoost](https://img.shields.io/badge/CatBoost-Gradient%20Boosting-yellow?style=for-the-badge)
![Kaggle](https://img.shields.io/badge/Kaggle-RMSE%200.12190-20BEFF?style=for-the-badge&logo=kaggle)
![Rank](https://img.shields.io/badge/Leaderboard-Rank%20723-blueviolet?style=for-the-badge)

</p>

An end-to-end Machine Learning pipeline developed for the **Kaggle House Prices: Advanced Regression Techniques** competition. This project demonstrates the complete workflow of building a high-performing regression model, from data preprocessing and feature engineering to ensemble learning and Kaggle submission generation.

---

# Table of Contents

- Project Overview
- Competition
- Results
- Repository Structure
- Dataset
- Project Workflow
- Exploratory Data Analysis
- Feature Engineering
- Data Preprocessing
- Model Selection
- Ensemble Learning
- Installation
- Usage
- Technologies Used
- Future Improvements
- Author

---

# Competition

**Competition:** House Prices: Advanced Regression Techniques

The objective is to predict the final selling price of residential homes using 79 explanatory variables describing different aspects of each property.

The competition evaluates submissions using **Root Mean Squared Error (RMSE)** on the logarithm of predicted house prices.

---

#  Results

## Final Performance

| Metric | Value |
|---------|-------|
| Evaluation Metric | RMSE |
| Final Kaggle Score | **0.12190** |
| Kaggle Leaderboard Rank | **723** |

### Highlights

- Extensive Feature Engineering
- Missing Value Handling
- Log Transformation
- Outlier Removal
- Ensemble Learning
- Weighted Prediction Blending
- Strong Kaggle Leaderboard Performance

---

# Repository Structure

```text
House-Prices-Prediction/
│
├──  Data/
│   ├── train.csv
│   └── test.csv
│
├──  output/
│   ├── .gitkeep
│   └── submission.csv
│
├──  house_prices_prediction.ipynb
│
├──  README.md
│
└──  .gitignore
```

---

# Dataset

The dataset consists of two CSV files.

| File | Description |
|------|-------------|
| train.csv | Training dataset containing features and SalePrice |
| test.csv | Test dataset without SalePrice |

Target Variable

```
SalePrice
```

Training Samples

```
1460
```

Testing Samples

```
1459
```

Total Features

```
79
```

---

#  Project Workflow

```text
                Kaggle Dataset
                       │
                       ▼
             Data Loading & Inspection
                       │
                       ▼
          Exploratory Data Analysis (EDA)
                       │
                       ▼
            Missing Value Analysis
                       │
                       ▼
            Feature Engineering
                       │
                       ▼
           Missing Value Imputation
                       │
                       ▼
      Log Transformation & Skewness Fix
                       │
                       ▼
              Outlier Removal
                       │
                       ▼
            One-Hot Encoding
                       │
                       ▼
          Model Benchmarking
                       │
                       ▼
        Cross Validation (10 Fold)
                       │
                       ▼
    CatBoost + XGBoost + LightGBM
                       │
                       ▼
        Weighted Ensemble Prediction
                       │
                       ▼
          Kaggle Submission File
```

---

#  Exploratory Data Analysis

The notebook begins with a comprehensive exploratory analysis of the dataset.

Performed analyses include:

- Missing value visualization
- Dataset inspection
- Feature distributions
- Understanding categorical and numerical variables

The missing values are visualized using a heatmap to identify highly sparse features before preprocessing.

> **Suggested Screenshot**

```
assets/missing_values.png
```

---

#  Feature Engineering

Feature engineering plays a significant role in improving model performance.

The notebook performs the following engineering steps:

### Highly Sparse Feature Removal

Columns containing more than **60% missing values** are removed.

### Domain Specific Features

New variables are created from existing information including:

- Total Square Footage
- Total Bathrooms
- Total Porch Area
- House Age
- Remodel Age
- Garage Age

These engineered variables provide richer information to the learning algorithms.

---

#  Data Preprocessing

Several preprocessing techniques are applied before model training.

## Missing Value Handling

### Numerical Features

Missing values are replaced using

- Median

### Categorical Features

Missing values are replaced using

- Mode
- None (where appropriate)

---

## Target Transformation

The target variable is transformed using

```python
np.log1p(SalePrice)
```

This reduces skewness and improves regression performance.

---

## Skewness Correction

Highly skewed numerical features are identified using statistical skewness.

Features with high skewness are transformed using

```python
log1p()
```

to make distributions more Gaussian.

---

## Outlier Removal

Extreme observations negatively affecting the regression model are removed before training.

This improves model stability and reduces prediction error.

---

## One-Hot Encoding

Categorical variables are converted into numerical format using

```python
pd.get_dummies()
```

Training and testing datasets are then aligned to ensure identical feature spaces.

---

# Model Selection

Multiple regression algorithms are benchmarked using **10-Fold Cross Validation**.

Models evaluated include:

- Linear Regression
- Ridge Regression
- Lasso Regression
- ElasticNet
- Decision Tree Regressor
- Random Forest Regressor
- Extra Trees Regressor
- Gradient Boosting Regressor
- Support Vector Regressor
- K-Nearest Neighbors
- XGBoost
- LightGBM
- CatBoost

The evaluation metric used is RMSE.

---

# Ensemble Learning

Instead of relying on a single model, predictions from multiple gradient boosting algorithms are combined.

## Models Used

- CatBoost Regressor
- XGBoost Regressor
- LightGBM Regressor

Final predictions are generated using weighted averaging, producing a more robust and accurate model than any individual learner.

---

## Submission

The final predictions are converted back from logarithmic scale and saved as

```text
output/submission.csv
```

Submission format

| Id | SalePrice |
|----|-----------|

---

# Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- SciPy
- Scikit-Learn
- XGBoost
- LightGBM
- CatBoost
- Kaggle Notebook

---

# Installation

Clone the repository

```bash
git clone https://github.com/adityajoshi1602/House-Prices-Advanced-Regression-Techniques.git
```

Move into the project directory

```bash
cd House-Prices-Prediction
```

Install dependencies

```bash
pip install -r requirements.txt
```

Run the notebook

```bash
jupyter notebook house_prices_prediction.ipynb
```

---

# Future Improvements

- Hyperparameter tuning using Optuna
- Bayesian Optimization
- Feature Importance using SHAP
- Recursive Feature Elimination
- Stacking Regressor
- Automated ML Pipelines
- Explainable AI (XAI)

---

# Key Learning Outcomes

- End-to-end Machine Learning workflow
- Data preprocessing techniques
- Feature engineering
- Handling missing values
- Skewness correction
- Ensemble learning
- Cross-validation
- Kaggle competition workflow
- Model evaluation using RMSE

---

#  Author

**Aditya Joshi**

---

## ⭐ If you found this project useful, consider giving the repository a star!