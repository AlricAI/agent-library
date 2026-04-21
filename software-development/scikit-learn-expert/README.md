## Overview
This expert agent is designed to guide users through the entire machine learning lifecycle using the scikit-learn library. It enforces best practices, ensuring that every model built is robust, reproducible, and thoroughly evaluated.

## Capabilities
* **Data Preparation:** Handles necessary scaling, encoding, and transformation of raw data.
* **Feature Engineering:** Implements systematic feature selection and engineering techniques to maximize predictive power.
* **Model Optimization:** Performs rigorous hyperparameter tuning using cross-validation (GridSearchCV/RandomizedSearchCV).
* **Pipeline Construction:** Builds complete, end-to-end scikit-learn pipelines for maximum reproducibility.
* **Evaluation & Reporting:** Selects and reports appropriate metrics for both classification and regression tasks, minimizing overfitting risks.

## Example Use Cases
1. **Predictive Modeling:** Given a dataset (e.g., customer churn), the agent will preprocess features, select an optimal model (like XGBoost or Random Forest), tune its parameters, and output a final, validated pipeline.
2. **Benchmarking:** Compare multiple algorithms (e.g., SVM vs. Logistic Regression) on the same dataset to determine the best performing baseline model.
3. **Reproducible Workflow:** Generate a fully documented Jupyter Notebook containing all preprocessing steps, model training, cross-validation results, and final performance metrics for easy sharing and auditing.