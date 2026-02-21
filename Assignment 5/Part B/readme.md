[Deployment Repository](https://github.com/RCC0149/wine-quality-pred-aws)

# ANA 680 – Assignment 5 (Part B)  
## Wine Quality Prediction – AWS SageMaker Deployment

**Author:** Randall C. Crawford
 
**Course:** ANA 680 – Machine Learning Deployment  

---

## Project Overview

This project demonstrates **cloud-native machine learning deployment using AWS services**, with a focus on **Amazon SageMaker** as a managed platform for training and inference. Assignment 5 (Part B) extends the deployment concepts from Part A by validating the ability to **train, package, and deploy a model within the AWS ecosystem** rather than via a container-only workflow.

The application predicts **wine quality scores** based on physicochemical attributes for red and white wines using a **Linear Regression model**. The emphasis of this assignment was on **AWS infrastructure integration**, not advanced model optimization.

---

## Model

- **Model Type:** Linear Regression  
- **Training Artifact:** `wine_model.pkl`  
- **Preprocessing Artifact:** `scaler.pkl`  

Linear regression was selected to:
- Provide a transparent, easily interpretable baseline
- Reduce deployment complexity
- Emphasize infrastructure and workflow correctness over model sophistication

---

## Dataset

- **Datasets:**
  - `winequality-red.csv`
  - `winequality-white.csv`
- **Source:** UCI Machine Learning Repository  
- **Features:** Physicochemical wine attributes  
- **Target:** Wine quality score  

The datasets were uploaded to **Amazon S3** and used as the authoritative data source for training and inference within AWS.

---

## AWS Deployment Architecture

The deployment leveraged multiple AWS services working together:

### Amazon S3
- Used for **persistent storage** of:
  - Training datasets
  - Model artifacts
- Acts as the handoff point between training and deployment stages

### Amazon SageMaker
- Used for:
  - Managed training execution
  - Model artifact handling
  - Deployment orchestration

SageMaker Studio / Notebook instances were used to:
- Load datasets from S3
- Train the Linear Regression model
- Serialize and save model artifacts back to S3
- Deploy the trained model to an inference endpoint

### Compute Configuration (CPU vs GPU)

- **CPU-based instances** were used for this project due to:
  - The simplicity of the Linear Regression model
  - Cost-efficiency considerations
- GPU-backed instances were not required, but SageMaker provides the flexibility to switch to GPU resources for more computationally intensive models (e.g., deep learning or large ensemble methods).

This decision reflects real-world deployment tradeoffs between **performance, cost, and workload requirements**.

---

## Training & Deployment Workflow

1. **Data Upload**
   - Raw datasets uploaded to Amazon S3
   - S3 paths referenced within SageMaker notebooks

2. **Model Training**
   - Training executed in a SageMaker-managed environment
   - Preprocessing and scaling applied consistently
   - Trained model serialized for reuse

3. **Model Registration**
   - Trained artifacts stored in S3
   - Prepared for deployment without retraining

4. **Model Deployment**
   - Model deployed as a SageMaker endpoint
   - Endpoint configured for real-time inference
   - AWS-managed scaling and availability

---

## Application Layer

A lightweight **Flask application** (`app.py`) is included to:
- Demonstrate how model artifacts can be consumed
- Provide a simple interface for passing inputs to the deployed model
- Bridge local interaction patterns with cloud-hosted inference services

---

## Repository Structure

```

├── app.py                     # Inference application
├── train_model.ipynb          # SageMaker training notebook
├── winequality-red.csv        # Red wine dataset
├── winequality-white.csv      # White wine dataset
├── scaler.pkl                 # Preprocessing scaler
├── wine_model.pkl             # Trained linear regression model
├── requirements.txt           # Python dependencies
└── templates/
└── index.html             # Web interface template

```

---

## Learning Outcome

This assignment demonstrates the ability to:
- Use **Amazon SageMaker** for managed ML workflows
- Integrate **S3** for dataset and model storage
- Select appropriate **compute resources (CPU vs GPU)** based on model needs
- Deploy trained models as scalable cloud endpoints
- Bridge local applications with managed cloud inference services

Assignment 5 (Part B) reinforces **cloud-first MLOps concepts**, complementing the container-based deployment explored in Part A.

---

