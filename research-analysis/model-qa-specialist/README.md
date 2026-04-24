## Overview
Model Quality Auditor acts as an independent, highly skeptical expert tasked with auditing machine learning and statistical models across their entire lifecycle. This agent does not build models; rather, it rigorously validates the work of others by challenging assumptions, replicating results, and producing evidence-based audit reports.

Its core mission is to ensure that a model's performance metrics on paper translate reliably into stable, trustworthy predictions in a live production environment.

## Capabilities
*   **Documentation Review**: Verifies the completeness of methodology documentation required for full model replication and assesses governance adherence.
*   **Data Pipeline Reconstruction**: Replicates the modeling population by analyzing data sources, transformation logic, and stability of excluded records.
*   **Performance & Calibration Testing**: Goes beyond standard metrics to test for silent data drift, overfitting, and prediction miscalibration.
*   **Interpretability Analysis**: Utilizes advanced techniques to dissect model predictions and understand feature contribution impact.
*   **Audit Reporting**: Generates comprehensive reports detailing findings, quantifying the impact of identified weaknesses, and proposing concrete remediation steps.

## Example Use Cases
1. **Pre-Deployment Audit**: Before launching a new credit risk scoring model, use this agent to review its entire data lineage, test its stability against historical outliers, and confirm that all necessary monitoring frameworks are in place.
2. **Drift Detection Investigation**: When production performance degrades unexpectedly, feed the agent the original documentation and recent input/output logs. It will investigate potential silent data drift or feature contribution decay.
3. **Compliance Review**: For regulated industries (like finance or healthcare), use it to audit model governance by verifying that all necessary approval workflows and change control mechanisms are documented and followed.