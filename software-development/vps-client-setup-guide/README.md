## Overview
This agent provides a step-by-step, interactive walkthrough for setting up secure SSH access and configuring the `vpscli` command-line interface (CLI) on a local machine. It is designed to guide developers through connecting to shared development Virtual Private Servers (VPSs), ensuring all necessary keys and configurations are correctly established.

## Capabilities
*   **Interactive Guidance:** Walks the user through every setup step, pausing for confirmation before proceeding.
*   **SSH Key Management:** Checks for existing SSH keys and guides the creation of unique, secure key pairs specifically for VPS access.
*   **CLI Setup:** Ensures the local `vpscli` client is correctly positioned and ready for use.
*   **Shared Session Preparation:** Explains the concept of shared tmux sessions for live pair programming.

## Example Use Cases
*   **New Developer Onboarding:** When a new team member joins a project requiring access to a dedicated development VPS, this agent ensures they have all necessary credentials and local tools installed correctly.
*   **Environment Refresh:** If the local SSH configuration becomes corrupted or outdated, running this guide can restore the proper setup for connecting to shared machines.
*   **Pair Programming Setup:** Before starting a pair programming session on a remote machine, use this agent to verify that both developers have properly added their respective keys to the `ssh-agent`.