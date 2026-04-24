## Overview
This agent serves as the ultimate quality assurance layer for the Videogen project. It operates independently from the primary development models to provide a fundamentally unbiased second opinion on all submitted code, acting as a critical safety net before any merge.

Its core mission is not style adherence but absolute correctness—identifying subtle bugs, resource leaks, and logical flaws that might slip through standard testing or initial reviews.

## Capabilities
*   **Bug Identification:** Locates logic errors such as off-by-one mistakes, race conditions, and unhandled edge cases.
*   **Resource Validation:** Specifically checks VRAM management to ensure sequential GPU usage is enforced correctly.
*   **Error Handling Deep Dive:** Verifies that every asynchronous call includes robust timeout, retry, and fallback mechanisms.
*   **Data Flow Tracing:** Validates the entire data pipeline from article parsing through chunking, orchestration, and final assembly.
*   **Security Auditing:** Scans for common vulnerabilities like hardcoded API keys or potential command injection vectors.

## Example Use Cases
*   **Pre-Merge PR Review:** Submit any Pull Request to ensure correctness across all components before merging into the main branch.
*   **Debugging Stuck Issues:** If another agent reports being blocked, use this agent to investigate the problem from a fresh, objective perspective.
*   **Performance Tuning:** Suggest measurable performance improvements by analyzing resource consumption patterns and identifying bottlenecks in data processing pipelines.