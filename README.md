Lung Cancer Prediction – End-to-End MLOps Project
Overview

This project demonstrates an end-to-end Machine Learning Operations (MLOps) workflow for predicting lung cancer risk based on patient health and lifestyle attributes. The objective is not only to train a machine learning model, but also to build a complete, production-ready system that includes experiment tracking, workflow orchestration, deployment, monitoring, and CI/CD following industry best practices.

The project is implemented as part of an MLOps capstone assignment and is designed to be reproducible, extensible, and cloud-ready.

Problem Description

Lung cancer is one of the leading causes of cancer-related deaths worldwide. Early detection can significantly improve treatment outcomes. The goal of this project is to build a binary classification model that predicts whether a patient is at high risk of lung cancer based on structured clinical and behavioral data.

The solution addresses the following challenges:

Reliable data preprocessing and feature handling

Reproducible model training with experiment tracking

Automated training workflows

Scalable model deployment

Continuous monitoring of model and data performance

Dataset

Source: Kaggle – Lung Cancer Prediction Dataset

Type: Tabular data (CSV)

Target variable: Lung cancer presence (binary)

Features include demographic information, smoking habits, and health indicators

The dataset is stored locally under:

data/raw/

Project Architecture

The system follows a modular architecture:

Data ingestion and preprocessing

Model training and evaluation

Experiment tracking and model registry

Workflow orchestration

Model deployment as a web service

Model and data monitoring

CI/CD automation

Technology Stack
Machine Learning

Python

Scikit-learn

Pandas, NumPy

MLOps

MLflow (experiment tracking and model registry)

Prefect (workflow orchestration)

Evidently (model and data monitoring)

Deployment

FastAPI (REST API)

Docker (containerization)

Cloud & Infrastructure

AWS (EC2, S3)

Terraform (Infrastructure as Code)

Engineering Best Practices

Pytest (unit and integration testing)

GitHub Actions (CI/CD)

Black / Ruff (formatting and linting)

Makefile

Pre-commit hooks

Repository Structure
lung-cancer-mlops/
│
├── data/
│   ├── raw/
│   └── processed/
│
├── src/
│   ├── data_loader.py
│   ├── features.py
│   ├── train.py
│   ├── evaluate.py
│   └── predict.py
│
├── pipelines/
│   └── training_pipeline.py
│
├── monitoring/
│   └── drift_report.py
│
├── api/
│   ├── app.py
│   └── schema.py
│
├── tests/
│   ├── test_features.py
│   └── test_api.py
│
├── terraform/
│   └── main.tf
│
├── .github/workflows/
│   └── ci.yml
│
├── Dockerfile
├── Makefile
├── requirements.txt
└── README.md

Model Training

Data is preprocessed and split into training and testing sets

A classification model (Logistic Regression / Random Forest) is trained

Evaluation metrics include accuracy, precision, recall, and F1-score

Trained models are logged and registered using MLflow

Experiment Tracking and Model Registry

MLflow is used to:

Track hyperparameters and metrics

Store trained model artifacts

Register and version models for deployment

Workflow Orchestration

Prefect orchestrates the training pipeline, including:

Data loading

Feature preprocessing

Model training

Evaluation

Model registration

This allows the pipeline to be run locally or in the cloud in a repeatable manner.

Model Deployment

The trained model is exposed through a REST API using FastAPI.

Key characteristics:

JSON-based input/output

Containerized using Docker

Can be deployed locally or on cloud infrastructure

Model Monitoring

Evidently is used to monitor:

Data drift

Feature distribution changes

Prediction drift

Monitoring reports are generated periodically and can be used to trigger retraining workflows if performance degrades.

CI/CD Pipeline

GitHub Actions is used to automate:

Code linting

Unit and integration tests

Build validation on every commit

This ensures code quality and prevents regressions.

How to Run the Project Locally
1. Clone the repository
git clone <repository-url>
cd lung-cancer-mlops

2. Install dependencies
make install

3. Run tests
make test

4. Train the model
python src/train.py

5. Start the API
uvicorn api.app:app --reload

Reproducibility

All dependencies are versioned in requirements.txt

Clear instructions are provided to run the project

Code is modular and testable

Infrastructure can be recreated using Terraform

Future Improvements

Add automated retraining based on monitoring alerts

Extend deployment to Kubernetes

Implement feature store integration

Add model explainability (SHAP)
