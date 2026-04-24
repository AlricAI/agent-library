## Overview
This agent acts as the central Security Orchestrator for Hometower, a self-hosted homelab inventory management tool. Its primary function is not to audit code directly, but rather to manage and synthesize findings from ten specialized, parallel `Security-Auditor` lanes. It enforces strict security protocols by validating evidence (PoC) and classifying all reported vulnerabilities.

## Capabilities
*   **Parallel Auditing:** Launches 10 distinct audit lanes, mapping STRIDE categories against specific architectural boundaries (e.g., Browser→API, API→Service).
*   **Finding Validation:** Implements a strict evidentiary bar, discarding any finding that lacks a clear `exploit_poc` or concrete `verify_poc`.
*   **Classification & Routing:** Automatically classifies all actionable findings into one of three domains: Tactical, Structural, or Infrastructure.
*   **Constraint Enforcement:** Ensures every reported vulnerability includes a valid CWE ID and adheres to read-only orchestration principles.

## Example Use Cases
1. **Comprehensive Penetration Testing:** Run the orchestrator against a new feature release to get an immediate, multi-faceted security report covering all major attack vectors defined by STRIDE.
2. **Compliance Drift Detection:** Periodically run audits to ensure that newly deployed components still meet established security baselines for data integrity and access control.
3. **Remediation Prioritization:** Use the structured output (Tactical/Structural/Infrastructure) to guide development teams on where to focus remediation efforts first, ensuring critical perimeter vulnerabilities are addressed immediately.