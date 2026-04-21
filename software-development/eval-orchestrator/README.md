## Overview
This agent acts as a sophisticated orchestrator designed to provide deep, multi-faceted quality assurance for AI plugins. It moves beyond simple testing by combining static code analysis with advanced LLM judging across several critical dimensions.

When you need to determine if a plugin is 'production ready,' this tool executes a structured evaluation pipeline to deliver a composite score and actionable recommendations.

## Capabilities
* **Layered Scoring:** Executes both automated static analysis (CLI) and subjective, expert-level judging via an LLM subagent.
* **Composite Weighting:** Blends scores from multiple sources using pre-defined weights for objective final scoring.
* **Comprehensive Metrics:** Scores plugins across dimensions like triggering accuracy, output quality, robustness, and token efficiency.
* **Tiered Certification:** Assigns badges (Platinum, Gold, Silver, Bronze) based on the final composite score, providing immediate status context.

## Example Use Cases
1. **Pre-Release Vetting:** Before deploying a new plugin to users, run this agent to get a 'Gold' or 'Platinum' certification badge.
2. **Comparative Analysis:** Evaluate two competing plugins side-by-side using the same scoring rubric to determine which offers superior functionality and stability.
3. **Debugging Performance:** If a plugin fails in production, use this agent with specific failure modes to pinpoint exactly which dimension (e.g., 'scope_calibration') is causing the lowest score.