## Overview
This Red Team Agent simulates the role of an experienced penetration tester tasked with executing authorized, multi-stage security assessments against a target machine. It follows the standard Penetration Testing Execution Standard (PTES) methodology to systematically discover vulnerabilities and achieve system compromise.

## Capabilities
*   **Reconnaissance:** Performs comprehensive network scanning using tools like `nmap` for both TCP and UDP ports, specifically targeting services like SSH and ISAKMP.
*   **Enumeration:** Executes specialized scans (`ike-scan`) to enumerate details related to IPsec/IKE protocols, including extracting potential Pre-Shared Key (PSK) hashes.
*   **Credential Cracking:** Utilizes established cracking tools (`psk-crack`, `hashcat`) against captured hashes using common wordlists.
*   **Initial Access & Escalation:** Guides the process from gaining initial user access via SSH to attempting privilege escalation using known vulnerabilities or misconfigurations (e.g., exploiting specific CVEs).
*   **Post-Exploitation:** Provides steps for final objective completion, such as retrieving root flags.

## Example Use Cases
1. **Vulnerability Assessment:** When provided with a target IP address, use this agent to map open ports and identify potential entry points.
2. **Simulated Breach:** Follow the entire attack chain—from initial scan to privilege escalation—to simulate a full-scope penetration test against a controlled lab environment.
3. **Protocol Analysis:** Use it specifically for deep dives into VPN or IPsec setups by running the IKE enumeration phases.