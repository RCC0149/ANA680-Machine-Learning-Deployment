[Deployment Repository](https://github.com/RCC0149/customer-churn-mlops-project)

# Customer Churn Prediction – MLOps Final Project

**Author:** Randall Crawford  
**Course:** ANA 680 – Machine Learning Deployment  

---

This project implements an end-to-end **MLOps pipeline** to predict customer churn in a subscription-based telecom business. The solution spans **data preparation, model training, containerization, CI/CD automation, cloud deployment, and orchestration**, integrating multiple modern deployment technologies.

The project culminates in a fully deployed and demonstrated machine learning system using **Flask, Docker, GitHub Actions, Heroku, AWS SageMaker, and Kubernetes**.

---

🗓️ **Timeline to Hit the Deadline (Sept 1, 2025, 2:00 AM CT)**

| Date            | Task                               |
|-----------------|------------------------------------|
| **Aug 25–26**   | Dataset download, EDA, cleaning    |
| **Aug 26**      | Model training and evaluation      |
| **Aug 26–27**   | Flask app + Dockerization          |
| **Aug 27–28**   | CI/CD pipeline + Heroku deployment |
| **Aug 28–?**    | SageMaker Lab + AWS deployment     |
| **Aug 29**      | Kubernetes deployment              |
| **Aug 30**      | Final demo prep, schedule Zoom     |

**---**

## ✅ Deliverables

- GitHub repo with clean code & organized folders  
- README.md with project explanation  
- `.ipynb` and `.pkl` files  
- Flask app and Docker container  
- CI/CD pipeline and live Heroku app  
- SageMaker notebook or screenshot  
- Kubernetes YAML files  

---

## 📁 Folder Structure (GitHub Repository)

```text
customer-churn-mlops-project/
│
├── data/
│   └── Telco-Customer-Churn-prepared.csv
│       # Prepared dataset (add to .gitignore if too large)
│
├── notebooks/
│   ├── ANA-680_FinalProject_EDA_8-30-2025.ipynb
│   │   # EDA, cleaning, feature engineering
│   └── ANA-680_FinalProject_Model_8-30-2025.ipynb
│       # Training, validation, metrics
│
├── app/
│   ├── app.py                          # Flask application
│   ├── models/
│   │   ├── churn_model.pkl             # Trained ML model
│   │   └── scaler.pkl                  # Feature scaler
│   ├── requirements.txt                # Python dependencies
│   ├── templates/
│   │   └── index.html                  # HTML form for predictions
│   ├── static/                         # (Optional) CSS, JS files
│   │   └── style.css
│   ├── Dockerfile                      # Containerize Flask app
│   ├── .dockerignore                   # Docker exclusions
│   ├── Procfile                        # Heroku deployment support
│   ├── .python-version                 # Python runtime specification
│   ├── heroku.yml                      # Docker-based CI/CD config
│   └── .github/
│       └── workflows/
│           └── main.yml                # GitHub Actions CI/CD workflow
│
├── kubernetes/
│   ├── deployment.yaml                 # Kubernetes deployment config
│   └── service.yaml                    # Kubernetes service config
│
├── sagemaker/
│   ├── maintenance.ipynb               # Endpoint cleanup & monitoring
│   ├── rebuild_model.sh                # Model artifact rebuild + S3 export
│   ├── train_model.ipynb               # Streamlined training for SageMaker
│   └── deploy_model.ipynb              # Container-based SageMaker deployment
│
└── README.md

# 📊 Customer Churn Prediction - MLOps Project

This project predicts customer churn in a subscription-based telecom business using a machine learning pipeline deployed through modern MLOps practices. The model is built, containerized, and deployed using tools such as Flask, Docker, GitHub Actions, Heroku, AWS SageMaker, and Kubernetes.

---

## 🚀 Objective

To build and deploy a predictive model that identifies customers likely to churn using historical data. This empowers the business to proactively engage at-risk customers and reduce churn.

---

## 📌 Dataset

- **Name:** Telco Customer Churn Dataset
- **Source:** [Kaggle Dataset Link](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)
- **Type:** Tabular, ~7,000 records
- **Target:** `Churn` (Yes/No)

---

## 🔧 Technologies Used

- **Data Processing:** `pandas`, `numpy`, `matplotlib`, `seaborn`
- **Modeling:** `scikit-learn`, `RandomForest`
- **Web Framework:** `Flask`
- **Containerization:** `Docker`, `Docker Hub`
- **CI/CD:** `GitHub Actions`, `Heroku`
- **Cloud ML Platform:** `AWS SageMaker Studio Lab`
- **Orchestration:** `Kubernetes`, `kubectl`, `minikube`

---

## 🔁 Workflow

1. **Data Exploration & Cleaning**
2. **Model Training & Evaluation**
3. **Save Model (.pkl)**
4. **Flask App for Local Deployment**
5. **Containerize with Docker**
6. **CI/CD Pipeline to Heroku using GitHub Actions**
7. **Redeploy using AWS SageMaker Studio Lab**
8. **Deploy with Kubernetes Cluster**

---

## 🧪 CI/CD Pipeline

- CI/CD is handled using **GitHub Actions**
- On every push to `main`, the model is tested, containerized, and deployed to **Heroku**
- Configuration is available in `.github/workflows/main.yml`

---

## ☁️ Cloud & Container Tools

| Tool       | Use Case                         |
|------------|----------------------------------|
| Docker     | Containerizing Flask application |
| Docker Hub | Image hosting                    |
| Heroku     | App deployment (via CI/CD)       |
| SageMaker  | Model deployment in AWS          |
| Kubernetes | Scalable app deployment          |

---

## 🧠 Model Performance

> *After model training and tuning...*

- Accuracy: `77.73%`
- F1 Score: `66.81%`
- Recall: `82.72%`

---

## ✅ To-Do Checklist

- [x] Select dataset & define problem
- [x] Perform EDA and data prep
- [x] Train and evaluate model
- [x] Build and test Flask app
- [x] Containerize app using Docker
- [x] Set up CI/CD and deploy on Heroku    https://telco-customer-churn-pred-44440b37f0f2.herokuapp.com/
- [ ] Redeploy via SageMaker
- [x] Deploy with Kubernetes
- [x] Final demo

---
