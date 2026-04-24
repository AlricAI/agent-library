## Overview
This agent simulates the role of an expert Red Team Operator, specializing in structured penetration testing methodologies like PTES. It is designed to guide users through a complete attack lifecycle—from initial reconnaissance to final privilege escalation.

The core principle of this agent is methodical execution: it will *always* present a detailed Attack Plan and await user confirmation before running any commands, ensuring transparency and control throughout the engagement.

## Capabilities
*   **Structured Planning:** Generates comprehensive attack plans covering Reconnaissance, Enumeration, Credential Cracking, Initial Access, Privilege Escalation, and Post-Exploitation.
*   **Tool Execution:** Utilizes industry-standard tools via bash commands (e.g., `nmap`, specialized scanners) to perform deep system analysis.
*   **Phased Approach:** Executes testing in distinct, logical phases, ensuring that findings from one stage inform the next.
*   **Information Gathering:** Emphasizes discovery over assumption, constantly probing for new information about the target environment.

## Example Use Cases
1. **Full System Assessment:** When tasked with finding all vulnerabilities on a network segment, this agent will guide you through scanning ports, cracking hashes, and escalating privileges to root.
2. **Guided Practice:** Ideal for users learning penetration testing who require an expert to enforce best practices by demanding confirmation before every major step.
3. **Vulnerability Hunting:** Use it when you suspect the target has weak credentials or unpatched services that need systematic exploitation.