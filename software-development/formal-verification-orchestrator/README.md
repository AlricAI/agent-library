## Overview
This agent acts as a comprehensive orchestrator for formal verification flows, managing the entire sequence from initial property planning through final sign-off. It systematically executes stages like Property Planning, Environment Setup, Formal Property Verification (FPV), Coverage Analysis, and Logical Equivalence Checking (LEC).

It adheres to strict loop-back rules—such as retrying FPV upon finding a Counterexample (CEX) or re-running LEC if unmatched points are found—to ensure thorough verification coverage.

## Capabilities
*   **Multi-Stage Workflow Management:** Executes defined stages: `property_planning` $\rightarrow$ `environment_setup` $\rightarrow$ `fpv_run` $\rightarrow$ `cex_analysis` $\rightarrow$ `lec_run` $\rightarrow$ `formal_signoff`.
*   **Tool Agnostic Execution:** Supports both open-source (e.g., Yosys, Boolector) and proprietary formal tools (e.g., JasperGold, VC Formal).
*   **Intelligent Loop Handling:** Implements defined retry logic for CEX discovery, vacuous proofs, and LEC mismatches.
*   **State Management:** Reads historical knowledge from `memory/formal/knowledge.md` and logs detailed session records to `memory/formal/experiences.jsonl` upon termination.

## Example Use Cases
1. **Full Design Sign-off:** Running the entire sequence when a design is considered feature-complete, aiming for zero unproven P0 properties and zero unmatched LEC points.
2. **Bug Triage:** When an initial FPV run yields a CEX, the agent can suspend, report the bug, and await manual RTL fixes before automatically retrying the verification loop.
3. **Equivalence Checking:** Verifying that the synthesized gate-level netlist perfectly matches the original Register Transfer Level (RTL) specification by running LEC.