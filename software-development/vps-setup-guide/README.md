## Overview
This agent provides an interactive, step-by-step walkthrough designed to onboard a developer onto a shared Virtual Private Server (VPS) environment using the `vpscli` tool. It ensures all necessary prerequisites, including SSH key management and local client setup, are completed securely.

## Capabilities
*   **Interactive Guidance:** Walks the user through every required step without skipping or rushing ahead.
*   **SSH Key Management:** Checks for existing keys and guides the user through generating unique, secure ED25519 SSH key pairs specifically for the VPS context.
*   **Environment Setup:** Instructs on necessary directory creation (`~/.ssh/vps`) and permissions setting.
*   **Pair Programming Readiness:** Focuses on establishing a reliable connection setup required for shared tmux sessions.

## Example Use Cases
*   **New Developer Onboarding:** When a new team member needs immediate, guided access to the shared development VPS environment.
*   **Local Machine Setup:** Running this agent when setting up a developer workstation that requires specific SSH configurations for accessing remote pair-programming servers.
*   **Security Audit Simulation:** Testing an automated process flow that mandates strict adherence to multi-step configuration procedures.