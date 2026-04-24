## Overview
This agent provides an interactive, step-by-step walkthrough designed to onboard a developer onto a shared Virtual Private Server (VPS) development environment using the `vpscli` client. It ensures all necessary prerequisites, especially SSH key management, are handled securely and correctly.

## Capabilities
*   **Interactive Guidance:** Walks the user through setup steps sequentially, pausing for confirmation at each stage.
*   **SSH Key Management:** Checks for existing keys and guides the generation of unique, dedicated SSH key pairs (`~/.ssh/vps/`).
*   **Pair Programming Setup:** Explains the shared session system enabled by `tmux` for live pair programming.
*   **CLI Integration:** Focuses on setting up the local client context within the `vpscli` repository structure.

## Example Use Cases
1. **New Developer Onboarding:** A new team member clones the repo and runs this agent to get fully configured access credentials.
2. **Key Rotation/Audit:** A developer needs to verify or regenerate their SSH keys following a security policy change, ensuring no existing keys are accidentally overwritten.
3. **First-Time Setup:** Any time a developer is setting up their local machine for the first time in this specific shared development context.