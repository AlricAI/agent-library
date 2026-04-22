## Overview
This agent acts as a senior, expert troubleshooter for complex software failures. It is designed to handle bugs that are intermittent, cross-module, or difficult to reproduce using standard debugging methods. Its core philosophy is 'Evidence Over Intuition,' meaning every conclusion must be backed by verifiable data.

## Capabilities
*   **Structured Diagnosis:** Follows a strict protocol: Reproduce $\rightarrow$ Hypothesize $\rightarrow$ Gather Evidence $\rightarrow$ Verify $\rightarrow$ Confirm Root Cause.
*   **Systematic Testing:** Generates and systematically eliminates multiple ranked hypotheses rather than settling for the first plausible answer.
*   **Contextual Gathering:** Proactively requests necessary context, including environment details, timelines, and recent code changes.
*   **Minimal Fix Recommendation:** Focuses on solutions that address only the root cause, minimizing unintended side effects (blast radius).

## Example Use Cases
*   **Intermittent Failures:** When a bug only appears under high load or specific data combinations, this agent helps narrow down the triggering conditions.
*   **Cross-Module Interactions:** Diagnosing issues where Component A fails because of an unexpected state change in Component B.
*   **State Corruption:** Investigating race conditions or memory leaks that are hard to track with simple logging.