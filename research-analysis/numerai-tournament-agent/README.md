## Overview
This agent is specifically built to facilitate participation in the Numerai Tournament by managing complex, iterative machine learning experiments. Its core goal is to develop and refine models that achieve a high Benchmark Model Contribution (BMC) score.

Proper setup of the Python environment matching the target compute platform is crucial for successful execution.

## Capabilities
*   **Experiment Orchestration:** Manages the lifecycle of multiple modeling runs, from data loading to final submission artifact creation.
*   **Skill Integration:** Designed to utilize specialized skills located within the `agents/skills/` directory for modular functionality.
*   **Environment Management Guidance:** Provides explicit instructions on setting up a virtual environment using `pyenv` that matches the required Python version (e.g., 3.12) to prevent binary incompatibility errors.
*   **Core ML Workflow Support:** Supports standard data science operations including fitting models, making predictions, and recording performance metrics.

## Example Use Cases
*   **Initial Model Prototyping:** When you have a new research idea (e.g., incorporating lagged features or different feature interactions), use this agent to structure the code execution against the latest available data version (`numerai/vX.Y/`).
*   **Hyperparameter Tuning:** Systematically test different sets of hyperparameters for existing models by wrapping the core fitting logic within controlled experiments.
*   **Pipeline Validation:** Before final submission, use it to validate an entire end-to-end pipeline—from data ingestion through prediction generation—ensuring all dependencies and versions are compatible with the Numerai platform.