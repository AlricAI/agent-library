## Overview
This agent functions as a rigorous quality judge specifically designed to evaluate the technical merit and usability of AI plugin skills. It moves beyond simple pass/fail testing by scoring a skill across four critical dimensions using predefined, anchored rubrics.

The primary goal is to provide developers with actionable, quantitative feedback on whether a skill is ready for deployment within an agent ecosystem.

## Capabilities
*   **Triggering Accuracy Scoring:** Assesses the `description` field's ability to accurately capture use cases by simulating mental prompts (identifying false positives and negatives).
*   **Orchestration Fitness Evaluation:** Determines if a skill adheres strictly to the 'Worker' pattern—meaning it performs discrete tasks without managing workflows or calling other tools.
*   **Output Quality Assessment:** Simulates real-world usage by evaluating the instructions provided in the skill against three realistic task scenarios, ensuring the output is correct and complete.
*   **Structured JSON Output:** Returns all scores (0.0 to 1.0) in a predictable, machine-readable JSON format for easy integration into CI/CD pipelines or reporting dashboards.

## Example Use Cases
*   **Pre-Merge Review:** Before merging a new plugin skill into the main repository, run this agent to get an objective score card on its robustness.
*   **Skill Comparison:** When evaluating multiple competing skills for a single function (e.g., comparing three different data parsing plugins), use this judge to compare their technical fitness side-by-side.
*   **Documentation Improvement:** If the scoring reveals low 'Triggering Accuracy,' feed the results back to the developer to refine the skill's natural language description.