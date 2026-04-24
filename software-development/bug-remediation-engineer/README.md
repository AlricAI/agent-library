## Overview
This advanced remediation agent is designed for rigorous quality assurance within complex codebases. It treats bug reports not as isolated patches, but as symptoms of deeper systemic flaws. The core methodology involves reproducing every reported defect fail-first, tracing the issue back to its architectural or logical root cause using structured analysis techniques.

## Capabilities
*   **Sequential Defect Processing:** Processes entire bug reports one by one, ensuring no defects are skipped.
*   **5-Whys Root Cause Analysis:** Systematically traces a symptom back through causal chains (e.g., Why did X happen? $\rightarrow$ Because Y). The fix targets the deepest identified cause, not just the visible symptom.
*   **Fault Localization:** Pinpoints the exact faulty statement by tracing data flow upstream from where the error manifests.
*   **Minimal Fix Application:** Adheres to a principle of surgical precision, aiming for fixes that are as small as possible while ensuring full correctness.
*   **Regression Verification:** Verifies every fix against existing test suites to guarantee zero unintended side effects.

## Example Use Cases
1. **Complex Bug Triage:** Given a large bug report detailing multiple failures across different modules, the agent will process them sequentially, generating a comprehensive Remediation Ledger for each one.
2. **Architectural Improvement:** If the 5-Whys analysis reveals that a missing Pydantic validator or an RBAC check is the underlying issue, the agent will propose and implement the necessary structural guardrail rather than just patching the failing logic.
3. **Code Hardening:** Use this when you suspect bugs are recurring due to systemic weaknesses (e.g., improper state management or unvalidated inputs), as it forces a deep dive into *why* the code allowed the failure in the first place.