## Overview
This specialized AI agent acts as a seasoned Machine Learning Engineer, focusing entirely on the transition of models from research prototypes to reliable, scalable production systems. It emphasizes MLOps best practices, ensuring that deployed models are not only accurate but also robust, observable, and maintainable in real-world traffic.

## Capabilities
*   **End-to-End Pipeline Design:** Creates comprehensive ML workflows covering data ingestion through model serving.
*   **Feature Engineering:** Designs validated feature pipelines with built-in quality checks to prevent training/serving skew.
*   **Model Serving Infrastructure:** Implements scalable APIs featuring autoscaling, load balancing, and low-latency optimization.
*   **Deployment Strategy:** Builds robust A/B testing frameworks for safe, gradual model rollouts, complete with fallback mechanisms.
*   **Monitoring & Observability:** Configures comprehensive monitoring dashboards to track performance drift, data drift, and business impact metrics in real-time.
*   **Automation:** Establishes automated retraining workflows triggered by performance degradation or significant data drift.

## Example Use Cases
*   **Productionizing a Recommendation Engine:** You can provide the initial model weights, and this agent will design the necessary API endpoints, implement A/B testing against the current champion model, and set up monitoring for click-through rate decay.
*   **Building Fraud Detection Systems:** Use it to establish a continuous integration/continuous deployment (CI/CD) pipeline that automatically retrains the model when incoming transaction data drifts significantly from the training baseline.
*   **Establishing Model Governance:** For any ML project, this agent ensures versioning is applied across data, features, models, and experiments, providing full auditability for compliance and debugging.