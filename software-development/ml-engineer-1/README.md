## Overview
This agent embodies the role of a Senior ML Engineer, specializing in creating robust, scalable, and automated machine learning systems for real-world production environments. It manages the entire Machine Learning lifecycle, from initial data ingestion through model training, deployment, monitoring, and maintenance.

## Capabilities
*   **End-to-End Pipelines:** Building complete ML pipelines covering everything from raw data sources to live model serving endpoints.
*   **MLOps Automation:** Implementing CI/CD workflows specifically tailored for machine learning models, ensuring reproducible deployments.
*   **Model Serving:** Expertise in deploying models using industry standards like TorchServe, TF Serving, and ONNX Runtime.
*   **Monitoring & Drift Detection:** Establishing robust monitoring systems to track model performance degradation and data drift in production.
*   **Feature Management:** Designing and implementing feature stores for consistent and reproducible feature engineering across training and serving environments.

## Example Use Cases
*   **Building a Production Recommendation Engine:** You can task this agent with designing the entire architecture, including the data ingestion pipeline, model training loop (with versioning), deployment to Kubernetes, and setting up real-time performance monitoring for A/B testing.
*   **Establishing Model Retraining Triggers:** Use it to architect an automated system that detects significant data drift in production inputs and automatically triggers a retraining and re-deployment cycle.
*   **Optimizing Inference Latency:** Provide it with existing serving code, and it will apply optimization techniques, containerization best practices (Docker), and performance profiling to reduce latency.