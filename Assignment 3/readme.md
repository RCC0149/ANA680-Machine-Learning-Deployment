# ANA 680 – Assignment 3  
## Telco Customer Churn Prediction  
### EDA, Feature Engineering, and Tuned ANN Model

**Author:** Randall C. Crawford  

**Course:** ANA 680 – Machine Learning Deployment  

---

## Assignment Overview

This assignment focuses on **end-to-end model development** for customer churn prediction using the **Kaggle Telco Customer Churn dataset**. The work includes **exploratory data analysis (EDA)**, **feature engineering**, and **training and tuning an Artificial Neural Network (ANN)**.  

---

## Dataset

- **Dataset:** Telco Customer Churn
- **Source:** Kaggle
- **Target:** Customer churn (binary: Stayed / Left)
- **Features:** Customer demographics, services, contract details, and billing information

---

## Exploratory Data Analysis (EDA)

A comprehensive EDA was performed to understand data quality and churn drivers:

- Assessment of class imbalance
- Distribution analysis of numeric features
- Categorical feature profiling
- Identification of churn-correlated variables
- Detection of data leakage risks and non-informative fields

EDA findings directly informed preprocessing and feature engineering decisions.

---

## Feature Engineering & Preprocessing

Key preparation steps included:

- Handling missing and inconsistent values
- Encoding categorical variables
- Scaling numeric features for neural network training
- Feature consolidation and cleanup
- Creation of a **cleaned, analysis-ready dataset** used consistently across experiments

---

## Model

- **Model Type:** Artificial Neural Network (ANN)
- **Framework:** TensorFlow / Keras
- **Objective:** Binary classification (Churn vs. No Churn)

The ANN architecture and training configuration were iteratively refined to balance **generalization, stability, and deployment readiness** rather than maximizing raw accuracy alone.

---

## Model Evaluation & Threshold Analysis

Model performance was evaluated using multiple metrics and **explicit decision threshold analysis** to balance precision and recall in a churn context.

### Key Performance Metrics (Selected Operating Point)

- **Accuracy:** 0.855  
- **Precision:** 0.649  
- **Recall:** 0.617  
- **F1 Score:** **0.633**  
- **ROC-AUC:** 0.766  
- **PR-AUC:** 0.488  
- **Specificity:** 0.915  

The **optimal threshold** (maximum F1-score) was identified at **0.612**, reflecting a deliberate tradeoff between false positives and false negatives :contentReference[oaicite:1]{index=1}.

### Confusion Matrix (Custom Threshold = 0.6)

|                | Predicted Stayed (0) | Predicted Left (1) |
|----------------|----------------------|--------------------|
| **Actual Stayed (0)** | 1460 | 135 |
| **Actual Left (1)**   | 155  | 250 |

This analysis demonstrates that **threshold selection is a critical deployment decision**, especially for churn use cases where intervention costs must be balanced.

---

## Final Model Selection

The tuned ANN was selected based on:
- Stable performance across validation runs
- Balanced precision–recall tradeoffs
- Explicit threshold controllability
- Suitability for downstream deployment

---

## Tools & Technologies

- **Python**
- **Pandas, NumPy**
- **TensorFlow / Keras**
- **scikit-learn**
- Jupyter Notebook

---

## Learning Outcome

This assignment demonstrates the ability to:
- Perform structured EDA for business-relevant ML problems
- Engineer features for neural network models
- Tune and evaluate ANNs using deployment-aware metrics
