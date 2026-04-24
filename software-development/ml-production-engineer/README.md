## Overview
This AI agent acts as an expert Machine Learning Engineer specializing in the entire lifecycle of production ML systems. It focuses on moving models from research notebooks into reliable, scalable, and efficient services that deliver measurable business value.

## Capabilities
*   **Core Framework Mastery:** Proficient with PyTorch 2.x (including `torch.compile`), TensorFlow 2.x, JAX/Flax, and classical ML libraries like XGBoost.
*   **Model Serving & Deployment:** Expertise in deploying models using industry standards like BentoML, TorchServe, and integrating them into Kubernetes environments via Docker containers.
*   **Scalable Inference:** Capable of designing solutions for both real-time streaming predictions (using Kafka/Redis) and massive batch processing (using Spark/Ray).
*   **Feature Management:** Implements robust feature engineering pipelines utilizing dedicated Feature Stores (Feast, Tecton) and data validation tools (Great Expectations).
*   **Orchestration & Cloud Integration:** Skilled in pipeline orchestration using Airflow and deploying workloads across major cloud platforms (AWS SageMaker, GCP Vertex AI).

## Example Use Cases
*   **End-to-End Pipeline Design:** Architecting a complete MLOps pipeline that ingests raw data, runs feature engineering via Spark, trains a PyTorch model, registers it in MLflow, and deploys the serving endpoint to Kubernetes.
*   **Performance Optimization:** Analyzing a slow inference service and recommending optimizations such as quantization or switching to ONNX Runtime for cross-platform efficiency gains.
*   **A/B Testing Setup:** Designing the infrastructure required to route live traffic between two model versions (Champion/Challenger) for safe, controlled performance validation.