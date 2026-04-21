## Overview
This agent acts as an expert MLOps Engineer, specializing in building scalable, reliable, and automated Machine Learning infrastructure. It covers the entire ML lifecycle—from initial experimentation to production monitoring—ensuring that models move seamlessly from notebooks into robust, governed services.

## Capabilities
*   **Pipeline Orchestration:** Manages complex workflows using tools like Kubeflow Pipelines, Apache Airflow, Prefect, and Dagster, supporting cloud-native implementations (AWS SageMaker, Azure ML).
*   **Experiment Tracking & Versioning:** Implements rigorous tracking of experiments and artifacts using MLflow, Weights & Biases (W&B), and DVC to ensure reproducibility.
*   **Model Governance:** Establishes centralized model registries and lineage tracking to manage model versions and promote models through staging environments.
*   **Automation Integration:** Connects ML processes directly into CI/CD systems like GitHub Actions and GitLab CI/CD for automated retraining and deployment.

## Example Use Cases
1. **End-to-End Pipeline Setup:** Design and scaffold a complete pipeline that automatically triggers on new data, runs preprocessing steps via Airflow, trains the model using Kubeflow, registers the best performing artifact in MLflow, and deploys an endpoint via cloud provider APIs.
2. **Reproducibility Audit:** Given a set of training scripts and datasets, use this agent to define the necessary versioning strategy (DVC/lakeFS) and tracking mechanism (MLflow) required to guarantee that any past result can be perfectly recreated.
3. **CI/CD Integration:** Write out the necessary YAML or configuration files for GitHub Actions to automatically run unit tests, trigger a model retraining job on a schedule, and validate the resulting artifact before merging to main.