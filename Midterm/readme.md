[Deployment Repository](https://github.com/RCC0149/student-performance-pred)

# ANA 680 – Midterm Project  
## Student Performance Prediction – Model Deployment Validation

**Author:** Randall C. Crawford  

**Course:** ANA 680 – Machine Learning Deployment  

---

## Project Purpose

This midterm project was designed to **validate machine learning deployment skills learned up to this point in the course**. The emphasis was on **end-to-end deployment mechanics**, including model serialization, API creation, environment configuration, and cloud hosting.

There was **no emphasis on exploratory data analysis (EDA) or extensive model determination**. The focus was on taking a reasonable model choice and **successfully deploying it as a production-style web service**.

---

## Project Overview

The application predicts **student academic performance** based on demographic and academic input features. A trained machine learning model is served via a **Flask web application** and hosted on **Heroku**, allowing users to submit inputs and receive real-time predictions.

---

## Dataset

- **Dataset:** Student Performance Dataset  
- **Source:** UCI Machine Learning Repository  
- **Target:** Student performance outcome  
- **Features:** Demographic, educational, and behavioral attributes  

The dataset was used primarily to support deployment validation rather than deep analytical exploration.

---

## Model

- **Model Type:** XGBoost Classifier  
- **Reason for Selection:**  
  - Strong out-of-the-box performance  
  - Robust handling of mixed feature types  
  - Well-suited for rapid deployment testing  

Basic hyperparameter tuning was performed to ensure reasonable predictive behavior, but **model optimization was not the primary objective** of this project.

The trained model and associated preprocessing artifacts were serialized and reused directly during deployment.

---

## Deployment Workflow

### 1. Application Setup (Flask)
- A Flask application (`app.py`) was created to:
  - Load the trained model (`model.pkl`)
  - Load the label encoder (`label_encoder.pkl`)
  - Accept user input via a web interface
  - Return model predictions

### 2. Deployment Configuration
The following files support deployment:
- `Procfile` – Defines the web process for Heroku  
- `requirements.txt` / `constraints.txt` – Python dependencies  
- `runtime.txt` – Runtime specification
- `templates/index.html` - Web service format 
- `.github/workflows/deploy.yml` – CI/CD deployment workflow  

### 3. Cloud Hosting (Heroku)
The Flask application was deployed to **Heroku**, validating:
- Environment reproducibility  
- Correct dependency installation  
- Reliable model inference in a hosted environment  

---

## Live Application

The deployed application is available at:

👉 **https://student-performance-pred-new-2941c0c64a82.herokuapp.com/**

Users can input student-related attributes and receive a predicted performance outcome directly through the web interface.

---

## Tools & Technologies

- **Python**
- **Flask**
- **XGBoost**
- **scikit-learn**
- **Heroku**
- **GitHub Actions (CI/CD)**

---

## Learning Outcome

This project demonstrates the ability to:
- Package trained machine learning models for deployment  
- Build and serve models using Flask  
- Configure and deploy applications to a cloud platform  
- Validate deployment pipelines independent of heavy modeling work  

The project serves as a **deployment readiness checkpoint**, ensuring core MLOps concepts were understood before advancing to more complex deployment scenarios.

---
