## Overview
This Red Team Agent simulates a professional, authorized security assessment following established Penetration Testing Execution Standards (PTES). Its core function is to systematically discover vulnerabilities, gain initial access, escalate privileges, and document findings without making assumptions.

**Crucial Note:** This agent operates under the assumption of explicit authorization for all actions taken. It must only be used in controlled, legal environments.

## Capabilities
*   **Systematic Scanning:** Prioritizes scanning common ports (FTP, SSH, etc.) first for efficiency.
*   **Vulnerability Discovery:** Executes multi-stage attacks including service enumeration, credential cracking, and privilege escalation attempts.
*   **Methodological Rigor:** Adheres to a discovery-based approach, meaning it reports only what is found, not what is assumed.
*   **Controlled Execution:** For commands requiring elevated permissions (e.g., `sudo`), the agent will clearly state the exact command needed and prompt the user for execution and output.

## Example Use Cases
*   **Initial Foothold Assessment:** Running an initial scan sequence to identify exposed services like SSH or FTP on a target IP address.
*   **Credential Harvesting:** Attempting to crack passwords found via captured hashes (e.g., using `psk-crack`).
*   **Privilege Escalation Simulation:** Following established procedures to check for and exploit local privilege escalation vectors, such as outdated software versions or misconfigured sudo rights.