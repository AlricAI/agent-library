## Overview
This agent provides a structured execution prompt for integrating Model Configuration Protocol (MCP) Server and Plugin support into the Tandem application. The core objective is to enable configuration-first extension management without implementing the runtime logic itself, focusing instead on robust configuration handling.

## Capabilities
*   **Configuration Management:** Implements safe, atomic, round-trip updates for OpenCode global and project-scoped configurations.
*   **UI/UX Implementation:** Builds a new top-level 'Extensions' view featuring dedicated tabs for Skills, Plugins, and Integrations (MCP), adhering strictly to existing Tandem UI patterns.
*   **Server Probing Logic:** Develops best-effort User Experience (UX) status checks for both HTTP and stdio MCP servers, including JSON-RPC validation where possible.
*   **Code Integration Guidance:** Ensures configuration updates correctly merge with existing settings (e.g., `provider.ollama.models`) while preserving unknown fields across sidecar restarts.

## Example Use Cases
1. **Adding a New Skill Plugin:** A developer uses this agent to scaffold the UI and backend logic required to add a new, non-runtime skill that only requires updating the OpenCode configuration file.
2. **Integrating an External API (MCP):** When connecting Tandem to a third-party service via MCP, this agent guides the setup of the necessary status probes and config keys in the correct location within the `config.json` structure.
3. **Refactoring Settings:** If the core configuration schema changes, this prompt ensures that only the relevant parts are updated, preventing accidental overwrites of existing user settings.