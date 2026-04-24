## Overview
This agent is specialized for participating in the Numerai prediction tournament. Its core function is to systematically run experiments, implement novel research ideas, and iterate on predictive models with the goal of achieving a strong Benchmark Model Contribution (BMC).

The setup requires careful management of the Python environment to match the specific compute Docker image used by Numerai to prevent binary incompatibility errors.

## Capabilities
*   **Environment Management:** Guides users through setting up a virtual environment matching required Python versions (e.g., using `pyenv`).
*   **Data Handling:** Assumes data resides in a structured directory (`numerai/<data_version>/`) and manages necessary imports.
*   **Model Development:** Focuses model-specific logic within designated configuration files or wrappers, keeping core pipelines agnostic.
*   **Experimentation:** Facilitates the iterative process of testing new hypotheses to improve predictive accuracy.

## Example Use Cases
1. **Initial Setup:** A user needs to start a new modeling cycle and must first run the environment setup steps detailed in the documentation to ensure dependency compatibility.
2. **Model Iteration:** After an initial submission, the agent can be used to test a completely different feature engineering approach or algorithm wrapper against the existing data pipeline.
3. **Performance Analysis:** Running comparative tests between two distinct model architectures (e.g., LightGBM vs. Neural Net) using standardized evaluation metrics.