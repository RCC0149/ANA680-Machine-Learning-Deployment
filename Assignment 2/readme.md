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
- **Support Vector Machines (Linear) - (Final Selection)**
- Support Vector Machines (RBF)

### Tree-Based and Ensemble Models
- Decision Tree
- Random Forest
- Gradient-Boosted Trees
- XGBoost

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

## Linear SVM Performance Evaluation

After final model selection, the **Linear Support Vector Machine (LinearSVM)** classifier was evaluated in detail to assess **threshold sensitivity, class tradeoffs, and deployment suitability**. Performance was examined across multiple decision thresholds to balance **precision, recall, and F1-score**, with particular emphasis on minimizing **false negatives** for malignant cases.

### Threshold Analysis

The table below summarizes LinearSVM performance across decision thresholds:

| Threshold | Accuracy | Precision | Recall | F1-score | ROC-AUC |
|---------|----------|-----------|--------|----------|---------|
| **0.10** | **0.977** | **0.934** | **1.000** | **0.966** | **0.997** |
| 0.20 | 0.977 | 0.949 | 0.982 | 0.966 | 0.997 |
| 0.30 | 0.960 | 0.946 | 0.930 | 0.938 | 0.997 |
| 0.40 | 0.966 | 0.964 | 0.930 | 0.946 | 0.997 |
| 0.50 | 0.966 | 0.981 | 0.912 | 0.945 | 0.997 |
| 0.60 | 0.954 | 0.980 | 0.877 | 0.926 | 0.997 |
| 0.70 | 0.949 | 0.980 | 0.860 | 0.916 | 0.997 |
| 0.80 | 0.937 | 0.979 | 0.825 | 0.895 | 0.997 |
| 0.90 | 0.920 | 1.000 | 0.754 | 0.860 | 0.997 |

- **Optimal threshold (maximum F1-score):** 0.10  
- **Maximum F1-score:** 0.966  
- **Accuracy:** 0.977  
- **ROC-AUC:** 0.997 (stable across all thresholds)

Lower thresholds favored recall, achieving **perfect recall at threshold 0.10**, while higher thresholds improved precision at the cost of missed malignant cases. This tradeoff was explicitly evaluated to support deployment decisions.

---

### Selected Operating Point

A **custom decision threshold of 0.10** was selected to prioritize recall while maintaining strong overall performance.

**Confusion Matrix (Threshold = 0.10)**

|              | Predicted Benign | Predicted Malignant |
|--------------|------------------|---------------------|
| Actual Benign | 114 | 4 |
| Actual Malignant | 0 | 57 |

At this threshold:
- **Zero false negatives** were observed  
- All malignant cases were correctly identified  
- A small number of false positives was accepted as a deliberate safety tradeoff  

This operating point reflects deployment priorities where **missing a malignant case is more costly than additional follow-up**.

---

### Feature Importance & Selection

To support interpretability and stability, **Recursive Feature Elimination (RFE)** and **permutation feature importance (F1-based)** were applied to the LinearSVM model.

Key observations include:
- A compact subset of features consistently ranked highly across methods  
- Permutation importance values showed low variance, indicating stable feature contributions  
- Feature importance was distributed across multiple predictors rather than dominated by a single feature  

This confirms that the LinearSVM decision boundary is supported by **multiple informative features**, improving robustness and interpretability.

---

### Deployment Justification

LinearSVM was selected and finalized for deployment because it:
- Achieved the **highest and most stable F1-score** among evaluated models  
- Maintained **perfect recall** at the selected operating threshold  
- Delivered **excellent ROC-AUC (0.997)**  
- Produced a simple, stable decision boundary suitable for deployment  
- Integrated cleanly into a lightweight, production-ready pipeline  

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

