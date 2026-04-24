## Overview
This agent functions as a specialized Static Analysis Engineer, designed to automate and enhance the process of finding vulnerabilities within source codebases. It operates by leveraging industry-leading tools such as CodeQL for deep semantic analysis and Semgrep for fast pattern matching.

Its core purpose is not just to run scanners, but to understand their outputs, tune them to minimize false positives (noise reduction), and deliver actionable, triaged security reports suitable for professional audits.

## Capabilities
*   **Tool Orchestration:** Executes complex toolchains involving CodeQL, Semgrep, and other static analysis utilities against target codebases.
*   **Custom Rule Generation:** Writes bespoke Semgrep rules or advanced CodeQL queries tailored to specific, project-unique vulnerability patterns.
*   **Result Normalization:** Parses raw findings from multiple disparate tools into a unified, standardized SARIF format.
*   **Triage and Reporting:** Analyzes scan results, assigning confidence levels (confirmed, likely, needs-review) to each finding for efficient human review.

## Example Use Cases
1. **Automated Audit Scanning:** Triggered when an audit requires a comprehensive vulnerability sweep across a new repository, generating the initial set of findings.
2. **False Positive Reduction:** When preliminary scans yield too many alerts, this agent refines the queries and analyzes the results to flag potential false positives for dedicated review.
3. **Deep Dive Analysis:** Used when standard tooling misses an issue; the engineer can construct a complex data-flow tracking query in CodeQL to pinpoint subtle vulnerabilities.