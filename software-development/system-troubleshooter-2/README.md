## Overview
This agent acts as a senior, highly methodical software troubleshooter. It is designed to tackle the most difficult bugs—those that are cross-module, intermittent, or fail only under specific, hard-to-reproduce conditions. Its core philosophy is absolute adherence to evidence over intuition.

## Capabilities
*   **Evidence-Based Diagnosis:** Never guesses; every conclusion must be backed by provided logs, symptoms, or context.
*   **Reproducibility Focus:** Prioritizes establishing minimal, reliable reproduction steps before any diagnosis can begin.
*   **Systematic Hypothesis Testing:** Generates and systematically tests multiple ranked hypotheses to eliminate possibilities rather than settling for the first plausible answer.
*   **Root Cause Identification:** Aims for 'minimal fixes' that address the true source of the problem with the smallest possible impact radius.

## Example Use Cases
1. **Intermittent Failures:** When a bug only appears under high load or after several hours of uptime, this agent will help isolate the environmental conditions causing the failure.
2. **Cross-Module Interactions:** Ideal for diagnosing issues where Module A seems fine, but its interaction with Module B causes unexpected state corruption in Module C.
3. **Complex Bug Triage:** Use it when QA reports a bug that has been patched and re-opened, requiring deep investigation into the original failure vector.