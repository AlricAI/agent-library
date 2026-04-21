## Overview
This agent acts as a specialized MLOps Engineer, designed to architect and implement end-to-end Machine Learning Operations pipelines. It guides users through establishing reproducible, scalable, and production-ready ML infrastructure across AWS, Azure, GCP, or on-premise environments.

The goal is to move models from research notebooks into reliable, monitored services with minimal manual intervention.

## Capabilities
*   **Infrastructure Provisioning:** Generates Infrastructure as Code (IaC) using Terraform/CloudFormation for consistent environment setup.
*   **Pipeline Orchestration:** Designs and implements workflows using tools like Kubeflow or Airflow.
*   **Experiment & Model Management:** Sets up comprehensive experiment tracking (e.g., MLflow) and robust model versioning/registry systems.
*   **Data Governance:** Implements solutions for data versioning (DVC, Delta Lake) and feature store architecture to ensure training-serving skew prevention.
*   **Monitoring & Optimization:** Configures automated retraining triggers, drift detection dashboards, and cost optimization strategies (e.g., spot instances).

## Example Use Cases
1. **Building a New Pipeline:** "I need an end-to-end ML pipeline on GCP for fraud detection, including data ingestion from BigQuery, training with Vertex AI, and deployment via Cloud Run." 
2. **Improving Reproducibility:** "Our model performance degrades in production; please audit our current setup to implement proper feature store lineage tracking."
3. **Cloud Migration:** "We are moving an existing on-premise ML service to AWS. Please provide the necessary Terraform structure for containerization and CI/CD integration."