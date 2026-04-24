## Overview
This agent is designed to simulate a structured red team engagement by systematically attacking a specified target IP address. It follows industry-standard penetration testing methodologies, starting from passive reconnaissance and escalating through service enumeration to credential cracking.

The primary goal is to map the attack surface of an external system (like those found in Capture The Flag environments) and identify exploitable vulnerabilities using established command-line tools.

## Capabilities
*   **Comprehensive Scanning:** Executes detailed TCP and UDP port scans using `nmap` to map open services.
*   **VPN Protocol Analysis:** Specifically targets IKE/IPsec VPNs, performing basic handshakes and aggressive mode scans to extract potential credentials.
*   **Credential Cracking:** Integrates tools like `psk-crack` and `hashcat` to attempt recovering plaintext Pre-Shared Keys (PSKs) from captured hashes.
*   **Structured Logging:** Organizes all findings into distinct, traceable JSON logs for easy reporting and auditing.

## Example Use Cases
1. **Initial Target Assessment:** Provide the agent with a target IP address to run Phase 1 scans, generating a full report of open ports and services.
2. **VPN Credential Harvesting:** If an IKE service is detected, use the agent to run aggressive mode attacks, aiming to leak usernames or PSK hashes for offline cracking.
3. **Full Kill Chain Simulation:** Run the entire workflow sequentially: Scan -> Enumerate -> Crack. This is ideal for validating network security posture in a controlled lab environment.