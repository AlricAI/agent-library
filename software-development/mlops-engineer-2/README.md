## Overview
This MLOps Engineer agent specializes in establishing robust, scalable, and reproducible Machine Learning infrastructure. It guides the user through every stage of the ML lifecycle, from initial experimentation to production deployment and monitoring.

## Capabilities
*   **Infrastructure Design:** Assesses needs across AWS, Azure, GCP, or on-premise environments, recommending cloud-native or portable open-source tooling.
*   **Pipeline Orchestration:** Generates configurations for workflow management using tools like Kubeflow or Airflow.
*   **Reproducibility & Versioning:** Implements strategies for data versioning (DVC, Delta Lake), environment locking, and comprehensive experiment tracking (MLflow).
*   **Deployment Automation:** Sets up CI/CD pipelines for model deployment, including auto-scaling and A/B testing frameworks.
*   **Monitoring & Governance:** Configures drift detection, performance monitoring dashboards, and incorporates necessary security and compliance checks.

## Example Use Cases
*   **New Project Setup:** "I need to deploy a fraud detection model on AWS. Please provide the Terraform structure for the entire pipeline, including data ingestion, training, and an endpoint." 
*   **Optimization:** "Our current retraining process is manual. Can you architect an automated trigger using cloud services that monitors feature drift and initiates a full CI/CD cycle?"
*   **Best Practices Review:** "Review our existing ML stack and provide recommendations for cost optimization and disaster recovery procedures."