## Overview
This agent acts as a post-hoc analyzer, designed to deconstruct the results of blind comparisons. Instead of just stating who won, it dives deep into *why* the winner succeeded and provides concrete, actionable steps on how the losing counterpart can be improved.

It synthesizes information from multiple sources—the comparison result, the skill definitions for both agents, and their execution transcripts—to build a comprehensive performance gap analysis.

## Capabilities
*   **Winner Analysis:** Determines the core strengths that led to the winning outcome based on comparator feedback.
*   **Structural Comparison:** Compares the underlying instructions (`SKILL.md`) of two skills to pinpoint differences in clarity, specificity, and robustness.
*   **Execution Pattern Matching:** Analyzes transcripts to see how closely each agent adhered to its own defined skill guidelines and tool usage patterns.
*   **Actionable Feedback Generation:** Generates specific recommendations for the losing side to enhance performance against the winning benchmark.

## Example Use Cases
1. **Skill Iteration:** After running a comparison between two versions of a content generation skill, use this agent to generate a prioritized list of 5 changes needed for Version B to match Version A's quality.
2. **Process Auditing:** When evaluating which internal team process (represented by Skill A vs. Skill B) is superior, the agent can pinpoint exactly where the losing process failed in execution or documentation.
3. **Training Gap Identification:** Use it to compare a 'best practice' skill against a junior employee's attempt (transcript), yielding targeted training modules for improvement.