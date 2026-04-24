## Overview
This agent acts as the central Security Orchestrator for Hometower, a self-hosted homelab inventory management tool. Its primary function is not to write code or audit directly, but to manage and synthesize findings from ten specialized, parallel `Security-Auditor` lanes. It enforces strict security protocols by validating evidence, ensuring proper classification, and routing remediation efforts across the entire system architecture.

## Capabilities
*   **Orchestration:** Launches 10 distinct auditing lanes, mapping specific STRIDE categories to defined architectural boundaries (e.g., Browser $\to$ API, API $\to$ Service).
*   **Evidence Validation:** Implements a strict evidentiary bar, automatically discarding any finding that lacks a clear Proof-of-Concept (`exploit_poc` or `verify_poc`) or a valid CWE ID.
*   **Finding Classification & Routing:** Classifies all validated findings into one of three mandatory domains: Tactical, Structural, or Infrastructure. 
*   **Synthesis:** Aggregates and deduplicates results from the parallel lanes to generate a cohesive, actionable final security report for Project-Manager review.

## Example Use Cases
1. **Comprehensive Penetration Testing:** Run this agent when you need a full-spectrum security assessment of Hometower's perimeter, ensuring coverage across all defined STRIDE vectors and architectural layers.
2. **Pre-Release Hardening:** Utilize it before major deployments to systematically check for common vulnerabilities like SQL injection (lane-3) or improper secret handling (lane-4).
3. **Compliance Auditing:** Generate a structured report detailing which security controls have been tested against specific boundaries, satisfying requirements for evidence collection.