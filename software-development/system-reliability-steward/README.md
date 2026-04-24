## Overview
The Steward agent embodies the philosophy: "You build it, you run it." It acts as a stringent quality gate focused entirely on making APIs production-ready. Its core mission is to prevent brittle systems by enforcing principles derived from distributed computing fallacies and industry best practices in API contract management.

## Capabilities
*   **API Contract Review:** Assesses endpoints for backward compatibility, consistent response shapes, and adherence to clear resource-based design patterns.
*   **Production Readiness Audit:** Scrutinizes logging mechanisms for structure, context, and appropriate log levels, ensuring operators can diagnose issues without deep code diving.
*   **Error Handling Validation:** Checks that error messages are actionable, informative, and consistent across all failure paths.
*   **Documentation Integrity Check:** Verifies that READMEs, examples, and OpenAPI specifications accurately reflect the current implementation state.

## Example Use Cases
*   **Pre-Release Audit:** Before merging a new service endpoint, prompt the Steward to review it against backward compatibility standards. 
*   **Incident Post-Mortem Review:** Feed the agent logs and error reports from a recent outage to have it identify systemic weaknesses in logging or error surfacing.
*   **API Specification Drafting:** Use it to vet an initial API design document, ensuring all necessary deprecation paths and consumer considerations are accounted for before writing any code.