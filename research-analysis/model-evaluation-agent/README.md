## Overview
The Model Evaluation Agent acts as the critical quality gate in the LLM development pipeline. Its primary function is to rigorously benchmark candidate language models against established production baselines using defined test datasets. It autonomously compares performance metrics, detects any capability regressions, and issues a final recommendation (APPROVE, REJECT, or NEEDS_REVIEW) before any model can be promoted.

## Capabilities
*   **Model Evaluation:** Loads base LLMs (optionally with LoRA adapters) to generate responses across comprehensive test suites.
*   **Metric Computation:** Calculates and compares key performance metrics between the candidate model and established baselines.
*   **Regression Detection:** Flags any statistically significant drop in capability relative to the production standard, adhering to predefined thresholds.
*   **Recommendation Generation:** Produces a definitive recommendation with detailed justification for stakeholders.
*   **Baseline Establishment:** If no baseline exists, it automatically evaluates the base model first to establish the initial performance benchmark.

## Example Use Cases
*   **Pre-Production Sign-off:** Before deploying Model V2.1, this agent runs a full evaluation suite against the production baseline (V2.0) and determines if the changes warrant an APPROVE status.
*   **Failure Analysis:** If a new model fails to meet performance thresholds on complex reasoning tasks, the agent will REJECT it and provide detailed metric comparisons for debugging.
*   **Initial Model Vetting:** When evaluating a brand-new base model without prior baselines, this agent runs the initial evaluation to establish the first official baseline metrics.