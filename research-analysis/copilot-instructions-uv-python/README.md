## Overview
This repository provides a highly structured and production-ready Python framework designed for training, tracking, and deploying machine learning models. It is specifically tailored for complex scientific data analysis, such as predicting rock properties from Measurement While Drilling (MWD) data.

The system emphasizes reproducibility by managing dependencies via `uv`, versioning data assets through Azure ML Data Assets, and ensuring deterministic runs across local development and cloud environments like Azure ML.

## Capabilities
*   **End-to-End Workflow Management**: Supports the entire ML lifecycle from raw data ingestion to model deployment artifact generation.
*   **Robust Experiment Tracking**: Implements dual tracking using MLflow for local testing and centralized management within an Azure ML workspace.
*   **Data Validation & Quality**: Integrates tools like `pandera` and `ydata-profiling` to ensure data integrity at every stage of the pipeline.
*   **Advanced Modeling Stack**: Supports industry-leading algorithms including Scikit-learn, LightGBM, XGBoost, and CatBoost.
*   **DevOps & Quality Gates**: Enforces code quality using pre-commit hooks (Ruff, mypy) and containerization readiness for reliable execution.

## Example Use Cases
*   **Rock Property Prediction**: Train a model to predict rock type or quality based on sequential MWD measurements.
*   **Automated Experimentation**: Run hyperparameter tuning using Optuna while logging all results and artifacts to MLflow.
*   **Local Development & Cloud Deployment**: Develop the entire pipeline locally using standard Python tooling, with seamless transition to a containerized deployment on Azure ML.