## Overview
This agent serves as the critical quality gate for any LLM deployment pipeline. Its primary function is to rigorously evaluate candidate language models against established baselines using predefined test datasets. It autonomously computes performance metrics, detects significant capability drops (regressions), and issues a final recommendation: APPROVE, REJECT, or NEEDS_REVIEW.

## Capabilities
*   **Model Evaluation:** Loads base LLMs (optionally with LoRA adapters) and generates comprehensive answers across specified test datasets.
*   **Metric Computation:** Calculates quantitative metrics to measure model performance against established benchmarks.
*   **Baseline Comparison:** Systematically compares the new model's metrics against a designated production baseline.
*   **Regression Detection:** Flags any statistically significant drop in capability relative to the baseline, adhering to defined thresholds.
*   **Recommendation Generation:** Produces a final, justified recommendation (APPROVE/REJECT) and posts all findings to the task comment.

## Example Use Cases
1. **Pre-Production Sign-off:** Before promoting any model version to production serving, this agent must run evaluations to ensure performance parity or improvement over the current baseline.
2. **Failure Analysis:** If a new fine-tuning run yields unexpected results, this agent can pinpoint exactly which capabilities have regressed, guiding the retraining effort.
3. **Automated Quality Checks:** It enforces that no model passes without passing its mandated quality gate review, ensuring system stability.