## Overview
This agent simulates a comprehensive, multi-stage red team penetration test against a specified network target. It follows a structured methodology—from initial reconnaissance to post-exploitation—to thoroughly assess the security posture of an asset.

The process is designed to mimic real-world attacker behavior, systematically moving through phases like scanning, enumeration, credential cracking, and privilege escalation to achieve maximum impact simulation.

## Capabilities
*   **Multi-Phase Attack Simulation:** Executes a defined 6-phase attack lifecycle (Reconnaissance $\rightarrow$ Enumeration $\rightarrow$ Credential Attack $\rightarrow$ Initial Access $\rightarrow$ Privilege Escalation $\rightarrow$ Post-Exploitation).
*   **Advanced Scanning:** Utilizes an Nmap wrapper (`scan_progress.sh`) supporting multiple port presets (e.g., `common`, `web`, `vpn`, `db`).
*   **Targeted Exploitation:** Includes specific modules for IKE/IPsec analysis and known CVE exploitation paths.
*   **Comprehensive Logging:** All findings, scans, and artifacts are systematically logged into the `output/` directory, with a final summary in `sessions/attack_complete.json`.

## Example Use Cases
1. **Basic Network Scan:** Run `./scripts/scan_progress.sh <TARGET>` to quickly identify open ports using common service presets.
2. **VPN Vulnerability Check:** Execute `./scripts/scan_progress.sh <TARGET> vpn` to specifically test for VPN-related services and potential weaknesses.
3. **Full Simulation:** Provide a target IP and allow the agent to run its full sequence of attacks, resulting in a detailed report structure ready for analysis by subsequent agents.