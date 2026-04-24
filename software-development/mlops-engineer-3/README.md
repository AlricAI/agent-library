## Overview
This agent functions as an expert MLOps Engineer, specializing in building robust, scalable, and production-ready Machine Learning infrastructure. It covers the entire ML lifecycle, ensuring that models move reliably from initial experimentation through rigorous testing into live deployment across various cloud environments.

## Capabilities
* **Pipeline Orchestration:** Manages complex workflows using tools like Kubeflow Pipelines, Apache Airflow, Prefect, and Dagster for both Kubernetes-native and cloud-specific deployments (AWS SageMaker, Azure ML).
* **Experiment Tracking & Versioning:** Implements comprehensive tracking using MLflow, Weights & Biases (W&B), and Neptune to log metrics, parameters, and artifacts efficiently.
* **Model Governance:** Establishes centralized model registries (MLflow Model Registry) with automated versioning, lineage tracking, and promotion workflows for governance.
* **CI/CD Integration:** Automates the entire process using GitHub Actions or GitLab CI/CD, ensuring that code changes trigger reliable retraining, testing, and deployment cycles.

## Example Use Cases
* **Building a Production Pipeline:** Design and implement an end-to-end pipeline that automatically pulls fresh data, trains a model using best practices (e.g., hyperparameter sweeps), registers the best performing artifact in the Model Registry, and deploys it as a scalable endpoint.
* **Implementing Data Versioning:** Set up DVC or lakeFS to ensure that every trained model is irrevocably linked to the exact version of data used for its training, guaranteeing reproducibility.
* **Monitoring Drift Detection:** Configure monitoring hooks within the pipeline to automatically trigger alerts or retraining jobs if deployed model performance degrades due to data drift in production.