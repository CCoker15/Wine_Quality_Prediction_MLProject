# Predicting Wine Quality with Machine Learning 🍷

### Project Overview
[cite_start]**Authors:** Chris Coker, Isaac Graham, Kate Kollman [cite: 226]
**Course:** STAT 335

This project applies machine learning techniques to predict the quality of Portuguese "Vinho Verde" wines based on physicochemical properties. [cite_start]By comparing linear baseline models against nonlinear gradient boosting methods, we aimed to identify the most significant chemical drivers of wine quality[cite: 231, 237].

---

### Hypotheses & Objectives
Based on our initial research, we tested the following hypotheses:
1.  [cite_start]**Alcohol Content:** We hypothesized that alcohol content is the primary positive driver of wine quality[cite: 209, 259].
2.  [cite_start]**Model Performance:** We hypothesized that nonlinear models (XGBoost) would significantly outperform linear models (Logistic Regression) due to complex interactions between chemical attributes[cite: 211, 262].

---

### Data Description
* [cite_start]**Source:** [UCI Machine Learning Repository - Wine Quality Dataset](https://archive.ics.uci.edu/dataset/186/wine+quality)[cite: 201].
* [cite_start]**Sample Size:** 6,497 observations (merged Red and White wine datasets)[cite: 202].
* [cite_start]**Features:** 11 continuous physicochemical variables (e.g., acidity, sugar, chlorides, pH, sulphates) and 1 binary variable for wine type[cite: 205, 246].
* [cite_start]**Target (Y):** Expert-assigned quality score (Ordinal scale 0–10)[cite: 206, 240].
* [cite_start]**Preprocessing:** Datasets were merged, measurement errors removed, and a binary 'wine_type' variable was added[cite: 252].

---

### Methodology & Model Training
[cite_start]We employed a Train-Validation-Test split strategy to ensure generalizability[cite: 215]. We trained and tuned three distinct model classes:

1.  **Multinomial Logistic Regression (Baseline):** Serves as a linear baseline for interpretation.
2.  [cite_start]**Ridge Logistic Regression (L2 Regularization):** Tuned via the `C` parameter (Best C=1.0) to handle multicollinearity[cite: 396, 399].
3.  [cite_start]**XGBoost (Gradient Boosting):** An advanced ensemble method used to capture nonlinear relationships and interaction effects[cite: 219, 438].

---

### Model Comparison & Evaluation
We evaluated models using **Accuracy**, **Weighted F1-Score**, and **Log Loss**.

| Model | Accuracy | Weighted F1 | Test Log Loss |
| :--- | :--- | :--- | :--- |
| **Baseline Logistic Regression** | ~54% | 0.51 | 1.08 |
| **Ridge Logistic Regression** | ~54% | 0.51 | 1.07 |
| **XGBoost (Final Model)** | **~68%** | **0.67** | **0.85** |

[cite_start]*[cite: 387, 388, 418, 419, 452, 456, 457]*

#### Key Findings:
* [cite_start]**XGBoost Superiority:** The XGBoost model outperformed the logistic baseline by **14% in accuracy**, confirming our hypothesis that nonlinear relationships are critical for predicting wine quality.
* [cite_start]**Feature Importance:** While alcohol was a top predictor, the XGBoost model identified **'wine_type'** as the most significant feature, followed by alcohol and volatile acidity[cite: 432, 433].
* **Class Imbalance:** All models struggled with rare quality scores (3, 4, 8, 9), but XGBoost showed improved recall for the minority classes compared to linear models[cite: 389, 439].

![Feature Importance](images/xgboost_feature_importance.png)
*Figure 1: XGBoost Feature Importance Plot *

---

### Conclusion & Future Work
Our analysis confirmed that nonlinear models better capture the complex chemical interactions that drive perceived wine quality[cite: 470]. While high alcohol content is strongly correlated with quality, it is not the sole driver; factors like wine type and volatile acidity play massive roles.

**Limitations:** The dataset lacks extreme quality values (very few 3s or 9s), making it difficult to predict outliers[cite: 301, 471].
**Future Work:** We recommend incorporating SHAP value analysis to better interpret the specific impact of interactions and expanding the dataset to include wines from diverse geographic regions[cite: 472].

---

### 📂 Files Included
* `notebooks/Wine_Quality_Analysis.ipynb`: Complete Python code for EDA, cleaning, and modeling.
* `reports/335_Final_Presentation(1).pdf`: Executive summary slide deck.
* `reports/Project_Proposal.pdf`: Original hypothesis and project plan.
