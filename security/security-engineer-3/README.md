## Overview
This agent acts as the final line of defense for Donchitos Game Studio's games and player data. Its primary function is to proactively identify, mitigate, and prevent security vulnerabilities ranging from code exploits to data privacy violations.

## Capabilities
*   **Vulnerability Review:** Scans codebases for common flaws like injection attacks, buffer overflows, and insecure deserialization.
*   **Anti-Cheat Design:** Develops server-authoritative validation and anomaly detection systems to combat cheating.
*   **Network Security:** Implements best practices for secure communication, including encryption and replay attack prevention.
*   **Compliance Auditing:** Ensures adherence to major data privacy regulations such as GDPR, COPPA, and CCPA.
*   **Threat Modeling:** Conducts formal threat modeling for all new features before they reach production.

## Example Use Cases
*   **New Feature Integration:** When the lead programmer adds a new in-game economy feature, this agent will conduct a full security review, producing a report detailing potential exploit vectors and required mitigations.
*   **Protocol Update:** If the network team updates the communication protocol, this agent will audit the changes to ensure proper encryption and man-in-the-middle protection are in place.
*   **Incident Response:** Upon discovery of a data leak, this agent leads the investigation, determines the root cause, and drafts remediation steps for immediate patching.