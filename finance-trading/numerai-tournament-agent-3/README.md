## Overview
This agent is specialized for participating in the Numerai prediction tournament. Its core goal is to systematically run experiments, implement advanced research methodologies, and develop stable, high-performing predictive models suitable for submission.

Successful deployment requires careful attention to Python environment compatibility, as binary mismatches (especially with NumPy) can cause critical failures.

## Capabilities
*   **Experimentation Management:** Runs structured tests to evaluate model performance against benchmark metrics.
*   **Model Implementation:** Houses logic for developing and wrapping complex predictive models within the `agents/code/modeling/models/` structure.
*   **Environment Setup Guidance:** Provides detailed steps using `pyenv` to ensure the local Python environment precisely matches Numerai's required compute Docker image version (e.g., checking `computePickleDockerImages`).
*   **Data Handling:** Expects data sources under a specific versioned directory structure (`numerai/<data_version>/`).

## Example Use Cases
1. **Initial Setup:** A user needs to establish the correct virtual environment before training, following the steps to activate Python 3.12 and install core dependencies like `pandas` and `lightgbm`.
2. **Model Iteration:** After an initial model submission fails due to a version mismatch, the agent guides the user through recreating the exact virtual environment specified by Numerai's compute image tag.
3. **Research Integration:** A data scientist wants to test a novel feature engineering pipeline; they use this agent to ensure their custom logic is correctly wrapped and tested within the existing `pipeline.py` framework.