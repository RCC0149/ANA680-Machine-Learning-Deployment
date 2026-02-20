# ANA 680 – Assignment 2  
## Exploratory Data Analysis, Model Selection, and Optimization  
### Wisconsin Breast Cancer Diagnostic Dataset

**Author:** Randall C. Crawford 

**Course:** ANA 680 – Machine Learning Deployment  

---

## Assignment Overview

This assignment establishes the **analytical and modeling foundation** for a production deployment completed in **Assignment 4**. The work includes **exploratory data analysis (EDA)**, **data cleaning**, **model benchmarking**, **hyperparameter optimization**, and **final model selection** using the **Wisconsin Breast Cancer Diagnostic (WBCD)** dataset.

✅ The final model selected here (**XGBoost**) is the **same model deployed in Assignment 4**.

---

## Dataset

- **Dataset:** Wisconsin Breast Cancer Diagnostic (WBCD)
- **Source:** UCI Machine Learning Repository
- **Observations:** 569
- **Features:** 30 numeric features derived from cell nucleus characteristics
- **Target Variable:**  
  - Malignant  
  - Benign  

A **cleaned and analysis-ready dataset** was generated as part of this assignment and used consistently across all modeling experiments.

---

## Exploratory Data Analysis (EDA)

Prior to modeling, a comprehensive EDA was performed to understand the structure and behavior of the data:

- Verification of data integrity and absence of missing values
- Examination of class balance between malignant and benign cases
- Distribution analysis of feature groups (mean, standard error, worst)
- Identification of feature scaling requirements
- Correlation analysis to assess multicollinearity
- Visual inspection of separability between classes

The EDA informed **preprocessing decisions**, **feature scaling**, and **model selection strategy**.

---

## Data Cleaning & Preparation

Based on EDA findings, the following steps were completed:

- Removal of non-informative identifier columns
- Standardization of numeric features where required
- Validation of target encoding
- Creation of a **cleaned dataset** used for all downstream modeling

This cleaned dataset ensured **reproducibility** and **consistency** across model evaluations and was later reused during deployment.

---

## Modeling Strategy

A deployment-oriented workflow was followed:

1. **Baseline Modeling**
   - Establish performance baselines using simpler classifiers
   - Assess interpretability and stability

2. **Advanced Model Evaluation**
   - Introduce non-linear and ensemble methods
   - Evaluate sensitivity to hyperparameters

3. **Hyperparameter Optimization**
   - Systematic tuning using cross-validation
   - Metric emphasis aligned with medical risk (false negatives)

4. **Final Model Determination**
   - Select a single, locked model configuration for deployment

---

## Models Tested and Optimized

The following model families were implemented, tuned, and evaluated:

### Linear and Probabilistic Models
- Logistic Regression
- Naive Bayes

### Distance- and Margin-Based Models
- k-Nearest Neighbors (KNN)
- Support Vector Machines (Linear and RBF)

### Tree-Based and Ensemble Models
- Decision Tree
- Random Forest
- Gradient-Boosted Trees
- **XGBoost (Final Selection)**

Each model was evaluated using consistent preprocessing, cross-validation, and classification metrics.

---

## Evaluation Metrics

Model comparison emphasized:
- Precision
- Recall
- F1-score
- Confusion matrix behavior

Accuracy alone was not used as a deciding factor due to the asymmetric cost of misclassification in a medical context.

---

## XGBoost Performance Evaluation

After final model selection, the XGBoost classifier was evaluated in detail to assess **threshold sensitivity, class tradeoffs, and deployment suitability**. Performance was examined across multiple probability thresholds to balance **precision, recall, and F1-score**, with particular emphasis on minimizing false negatives for malignant cases.

### Threshold Analysis

The table below summarizes XGBoost performance across decision thresholds:

| Threshold | Accuracy | Precision | Recall | F1-score | ROC-AUC |
|---------|----------|-----------|--------|----------|---------|
| 0.10 | 0.863 | 0.704 | 1.000 | 0.826 | 0.996 |
| 0.20 | 0.943 | 0.851 | 1.000 | 0.919 | 0.996 |
| 0.30 | 0.960 | 0.891 | 1.000 | 0.942 | 0.996 |
| 0.40 | 0.971 | 0.919 | 1.000 | 0.958 | 0.996 |
| 0.50 | 0.977 | 0.949 | 0.982 | **0.966** | 0.996 |
| 0.60 | 0.977 | 0.949 | 0.982 | 0.966 | 0.996 |
| 0.70 | 0.966 | 0.947 | 0.947 | 0.947 | 0.996 |
| 0.80 | 0.937 | 0.942 | 0.860 | 0.899 | 0.996 |
| 0.90 | 0.897 | 1.000 | 0.684 | 0.812 | 0.996 |

- **Optimal threshold (maximum F1-score):** 0.50  
- **Maximum F1-score:** 0.966  
- **ROC-AUC:** 0.996 (stable across all thresholds)

Lower thresholds favored recall, achieving perfect recall at thresholds ≤ 0.4, while higher thresholds improved precision at the cost of missed malignant cases. This tradeoff was explicitly evaluated to support deployment decisions.

---

### Selected Operating Point

A **custom decision threshold of 0.4** was also evaluated to prioritize recall while maintaining strong overall performance.

**Confusion Matrix (Threshold = 0.4)**

|              | Predicted Benign | Predicted Malignant |
|--------------|------------------|---------------------|
| Actual Benign | 113 | 5 |
| Actual Malignant | 0 | 57 |

At this threshold:
- **Zero false negatives** were observed
- All malignant cases were correctly identified
- A small increase in false positives was accepted as a deliberate tradeoff

This operating point highlights that **threshold selection is a critical deployment decision**, not merely a post-processing step.

---

### Feature Importance

To assess model interpretability and stability, **permutation feature importance (F1-based)** was computed and compared with native XGBoost feature importance.

Key observations include:
- Multiple features contributed meaningfully to model performance
- No single feature dominated predictions
- Low standard deviation across permutation importance scores indicates stable feature rankings

This confirms that the model’s decisions are **distributed across multiple predictive features**, reducing reliance on spurious correlations.

---

### Deployment Justification

XGBoost was selected and finalized for deployment because it:
- Achieved the **highest F1-score** among all evaluated models
- Maintained **excellent ROC-AUC (0.996)** across thresholds
- Allowed **explicit threshold control** for deployment risk management
- Demonstrated stable and interpretable feature importance
- Generalized well without sacrificing recall on malignant cases

The selected model configuration and decision threshold were **locked and reused unchanged** in **Assignment 4 (Deployment)**.


---

## Relationship to Assignment 4 (Deployment)

- **Assignment 2:** EDA, data cleaning, model benchmarking, optimization, and selection  
- **Assignment 4:** Deployment and serving of the selected model  

This separation mirrors real-world machine learning workflows, where **data understanding and model determination precede deployment**.

---

## Tools & Technologies

- **Python**
- **scikit-learn**
- NumPy, Pandas
- Jupyter Notebook

---

## Notes

This assignment demonstrates that reliable deployment depends on:
- Careful data understanding through EDA
- Clean, reproducible datasets
- Disciplined model optimization and comparison
- Selecting models based on **risk-aware metrics**, not accuracy alone

