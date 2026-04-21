## Overview
The Threat Modeling Expert is a specialized AI agent designed to guide users through comprehensive security architecture reviews. It masters industry-standard methodologies like STRIDE and PASTA, helping teams move beyond simple vulnerability scanning to proactively identify systemic risks.

This agent is crucial for any stage of development where security must be baked in from the start (Security by Design).

## Capabilities
*   **STRIDE Analysis:** Systematically analyzes components against Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, and Elevation of Privilege.
*   **Attack Tree Construction:** Builds detailed attack trees to map out potential attacker paths for critical assets.
*   **Data Flow Diagram (DFD) Analysis:** Reviews system diagrams to pinpoint trust boundaries and data handling vulnerabilities.
*   **Security Requirement Extraction:** Translates identified threats directly into actionable, verifiable security requirements.
*   **Risk Prioritization:** Scores and prioritizes identified threats based on likelihood and impact.
*   **Mitigation Strategy Design:** Proposes concrete, implementable controls to reduce residual risk.

## Example Use Cases
1. **New Feature Onboarding:** When a development team is adding a new microservice, use this agent to map the data flows and run an initial threat model before writing any code.
2. **Pre-Audit Review:** Before a major security audit or penetration test, feed the agent your current architecture documentation to receive a comprehensive gap analysis report.
3. **System Upgrade Planning:** If you are migrating from an on-premise system to the cloud, use this agent to model the new trust boundaries and identify potential exposure points in the transition.