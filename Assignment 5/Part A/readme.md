[Deployment Repository](https://github.com/RCC0149/wine-quality-pred)

# ANA 680 – Assignment 5 (Part A)  
## Wine Quality Prediction – Containerized Cloud Deployment

**Author:** Randall C. Crawford  

**Course:** ANA 680 – Machine Learning Deployment  

---

## Project Overview

This project demonstrates **container-based deployment of a machine learning application**. The objective of Assignment 5 (Part A) was to validate the ability to **package a trained model and inference application into a Docker container** and deploy that container to a **cloud-hosted production environment**.

The application predicts **wine quality scores** for red and white wines based on physicochemical attributes. The emphasis of this assignment was on **containerization and deployment**, not exploratory data analysis or extensive model development.

---

## Application Description

The deployed application is a **Flask-based web service** that:
- Accepts wine attribute inputs through a web interface
- Applies the same preprocessing used during model training
- Returns a predicted wine quality score

All application code, dependencies, and model artifacts are encapsulated within a **Docker container**, ensuring consistent behavior across development and production environments.

---

## Model

- **Model Type:** Random Forest Classifier  
- **Training Script:** `train_model.py`  
- **Serialized Artifacts:**
  - `wine_model.pkl` / `models/wine_model.joblib`
  - `scaler.pkl` / `models/scaler.joblib`

The Random Forest classifier was chosen and tuned to provide reliable performance and robustness while keeping the focus on **deployment mechanics** rather than model experimentation.

---

## Model Inputs

The model expects the following physicochemical wine characteristics:

- Fixed acidity  
- Volatile acidity  
- Citric acid  
- Residual sugar  
- Chlorides  
- Free sulfur dioxide  
- Total sulfur dioxide  
- Density  
- pH  
- Sulphates  
- Alcohol  

---

## Deployment Workflow

### Containerization (Docker)

Docker was used to:
- Package the Flask application
- Bundle model and preprocessing artifacts
- Lock Python dependencies and runtime behavior
- Create a portable, reproducible container image

This container served as the **single deployable unit** for the application.

### Cloud Deployment (Heroku)

The Docker container was deployed to **Heroku**, validating:
- Container-based deployment workflows
- Hosted inference using a Flask web application
- Environment consistency between local build and cloud runtime

---

## Live Application

👉 **https://wine-quality-pred-068f95e304e6.herokuapp.com/**

---

## Learning Outcome

This assignment demonstrates the ability to:
- Containerize machine learning applications using Docker
- Deploy containers to a cloud hosting platform
- Serve machine learning models via a web interface
- Manage dependencies and runtime environments consistently

Assignment 5 (Part A) serves as a **container-based deployment validation**, reinforcing practical MLOps skills prior to more advanced deployment scenarios.

---
