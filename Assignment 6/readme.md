[Deployment Repository](https://github.com/RCC0149/iris-knn-pred)

# ANA 680 – Assignment 6  
## Iris Classification with Flask, Docker, and Kubernetes (Local Deployment)

**Author:** Randall C. Crawford  

**Course:** ANA 680 – Machine Learning Deployment  

---

## Project Overview

This assignment demonstrates **local deployment of a machine learning application using containerization and Kubernetes orchestration**. The objective was to validate an understanding of **model serving, containerization, and Kubernetes-based deployment**, rather than cloud hosting.

A **K-Nearest Neighbors (KNN)** classifier was trained on the **Iris dataset** and served via a **Flask web application**. The application was first containerized with **Docker**, then deployed locally to a **Kubernetes cluster using Minikube**.

This assignment emphasizes **deployment mechanics and orchestration concepts**, not exploratory data analysis or advanced model selection.

---

## Application Description

The application provides a simple **HTML-based interface** that allows users to input Iris flower measurements and receive a predicted class:

- *Iris-setosa*
- *Iris-versicolor*
- *Iris-virginica*

The full inference pipeline (model loading, input validation, prediction, and response rendering) is handled by a Flask application running inside a container.

---

## Model

- **Model Type:** K-Nearest Neighbors (KNN)
- **Training Split:** 70% training / 30% testing
- **k:** 3
- **Observed Accuracy:** 1.0 on the test set
- **Model Artifact:** `iris_knn_model.pkl`

The model was trained once and serialized for reuse during deployment. Model complexity was intentionally kept low to maintain focus on **deployment workflows**.

---

## Dataset

- **Dataset:** Iris Dataset
- **Source:** UCI Machine Learning Repository
- **Features:**
  - Sepal length
  - Sepal width
  - Petal length
  - Petal width

Input validation enforces realistic value ranges for each feature to ensure consistent inference behavior.

---

## Deployment Architecture

This assignment followed a **progressive local deployment workflow**:

### 1. Flask Application
- Flask used to serve the model and HTML interface
- Validates user inputs
- Loads the serialized model at runtime
- Returns predicted class labels

### 2. Containerization (Docker)
- The Flask application and model artifacts were packaged into a Docker image
- Ensures reproducible runtime behavior
- Eliminates dependency conflicts across environments

### 3. Orchestration (Kubernetes with Minikube)
- The Docker image was deployed to a **local Kubernetes cluster**
- **Minikube** was used to simulate a production-like Kubernetes environment
- A **Deployment** resource manages application pods
- A **Service (LoadBalancer)** exposes the application locally

This approach mirrors production orchestration patterns without requiring cloud infrastructure.

---

## Local Deployment Context

- **Deployment Type:** Local (not cloud-hosted)
- **Operating System:** Windows 11
- **Shell:** PowerShell
- **Container Runtime:** Docker Desktop
- **Kubernetes:** Minikube (local cluster)

Local deployment was intentionally used to focus on **Kubernetes fundamentals**, including pod management, service exposure, and container orchestration.

---

## Repository Structure

---

├── app/
│ ├── model/
│ │ └── iris_knn_model.pkl
│ ├── templates/
│ │ └── index.html
│ ├── app.py
│ ├── Dockerfile
│ ├── deployment.yaml
│ ├── service.yaml
│ ├── requirements.txt
├── data/
│ └── iris.data
└── train_model.py

---

---

## Learning Outcome

This assignment demonstrates the ability to:
- Serve machine learning models via a web application
- Containerize ML applications using Docker
- Deploy and manage applications using Kubernetes
- Expose services locally through Kubernetes networking
- Apply production-style deployment patterns without cloud infrastructure

Assignment 6 reinforces **core MLOps and orchestration concepts**, providing a strong foundation for cloud-native deployments explored later in the course.

---

