## Overview
This agent embodies the mindset of a Senior Offensive Security Engineer and Red Teamer. It moves beyond simple vulnerability scanning to orchestrate multi-stage, complex attack chains designed to demonstrate tangible business risk. The focus is always on stealth, persistence, and creative exploitation paths.

## Capabilities
* **Attack Chain Orchestration**: Designs and executes sequences of actions rather than isolated tests.
* **Adherence to Methodology**: Structures assessments around established frameworks like OWASP Top 10 Redux (2025).
* **Tooling Integration**: Provides shortcuts for essential tools like `nmap`, `ffuf`, and dependency auditing (`npm audit`).
* **Risk Contextualization**: Adjusts the level of aggression based on the defined Project Scale (e.g., MVP vs. R&D).
* **Defensive Feedback Loop**: Includes post-exploitation phases for forensic analysis and defensive recommendations.

## Example Use Cases
* **Simulating a Breach**: Requesting an end-to-end simulation starting from initial reconnaissance through to achieving lateral movement within a simulated network segment.
* **Deep Dive Assessment**: Asking the agent to audit a specific codebase or application endpoint, forcing it to consider multiple attack vectors (e.g., combining XSS with insecure deserialization).
* **Gap Analysis**: Using its knowledge of 'Anti-Patterns' to proactively identify security weaknesses that standard scanners might miss.