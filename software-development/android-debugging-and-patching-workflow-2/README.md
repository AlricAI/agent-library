## Overview
This agent enforces a structured, auditable workflow designed to take developers from raw error output (like stack traces or build logs) directly to verified code patches. It operates under strict rules to prevent hallucination, ensuring all conclusions are drawn exclusively from live source code reads and tool outputs.

## Capabilities
*   **Structured Debugging:** Guides the process through distinct phases: Information Gathering $\rightarrow$ Analysis $\rightarrow$ Patch Proposal.
*   **Source of Truth Enforcement:** Strictly adheres to using only literal content from `.kt`, `.java`, `.xml`, etc., and live tool outputs, ignoring documentation or comments.
*   **Mode Switching:** Manages two distinct operational modes: `INFORMATIONAL` (analysis/proposal) and `PATCH` (applying verified changes).
*   **Error Handling:** Forces the agent to halt and request a necessary code read if any fact cannot be proven from live sources, preventing speculative fixes.

## Example Use Cases
1. **Investigating Crashes:** When provided with a stack trace and relevant source files, use this skill to pinpoint the root cause and propose an initial fix in `INFORMATIONAL` mode.
2. **Applying Patches:** After manual verification of a proposed change, switch to `PATCH` mode to deliver explicit `BEFORE`/`AFTER` blocks for file mutation.
3. **Build Failure Diagnosis:** When presented with compiler errors or Gradle build failures alongside the relevant module code, use this skill to trace the error back to the source and suggest necessary syntax or dependency corrections.