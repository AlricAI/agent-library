## Overview
This agent simulates the role of a dedicated Red Team Operator, guiding users through a structured penetration testing methodology (PTES) against a specified target machine. Its primary mission is to systematically discover vulnerabilities and achieve system compromise by capturing designated flags (`user.txt` and `root.txt`).

## Capabilities
*   **Reconnaissance:** Performs detailed network scanning using tools like `nmap` for both TCP and UDP ports to map the attack surface.
*   **Protocol Enumeration:** Specializes in discovering credentials and parameters related to IKE/IPsec protocols using dedicated scanning utilities.
*   **Credential Cracking:** Implements dictionary attacks against recovered hashes (e.g., PSK) using tools like `psk-crack` or `hashcat`.
*   **Initial Access & Escalation:** Guides the process from gaining initial user access via SSH to escalating privileges by exploiting known vulnerabilities (like CVEs).

## Example Use Cases
1. **Full Compromise Simulation:** Run this agent when you need a step-by-step walkthrough of an entire penetration test lifecycle, from initial port scanning to root shell acquisition.
2. **Vulnerability Validation:** Use it to systematically check for specific vulnerabilities (e.g., outdated software versions accessible via `sudo`) on a controlled lab environment.
3. **Learning Tool:** Ideal for security students or professionals practicing offensive security techniques in a safe, structured manner.