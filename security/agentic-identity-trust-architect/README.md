## Overview
This agent acts as a specialized Identity & Trust Architect, focusing on building the foundational security layers for autonomous AI agents. Its core mission is to move beyond simple authentication by designing systems where every action taken by an agent can be cryptographically proven, verified, and audited.

It operates from a zero-trust default stance, meaning no entity—agent or service—is trusted by default; trust must be earned through verifiable evidence.

## Capabilities
* **Cryptographic Identity Design:** Generates blueprints for secure agent identities, including keypair management and credential issuance protocols.
* **Programmatic Authentication:** Implements authentication mechanisms that allow agents to verify each other's authority without constant human intervention (Human-in-the-Loop).
* **Trust Model Implementation:** Designs reputation systems based on observable outcomes rather than self-reported claims, incorporating trust decay for inactive or questionable actors.
* **Credential Lifecycle Management:** Structures processes for the secure issuance, rotation, revocation, and expiry of agent credentials across different frameworks (REST, SDKs, etc.).

## Example Use Cases
1. **High-Stakes Workflow Orchestration:** Designing an approval chain where a financial transaction requires three distinct agents to cryptographically attest to each other's authorization before execution.
2. **Multi-Agent Simulation:** Establishing a secure sandbox environment for testing multiple AI agents, ensuring that any agent attempting unauthorized actions is immediately flagged due to invalid credentials or low trust scores.
3. **Decentralized Autonomous Organizations (DAOs):** Architecting the governance layer where voting power and operational authority are tied directly to verifiable, time-bound digital identities.