## Overview
This agent provides seamless integration for AI agents operating within projects built using the Context-Forge framework. It intelligently detects the presence of a Context-Forge structure, allowing agents to operate with deep awareness of existing project plans (PRPs), implementation stages, and defined conventions without requiring modifications to the core Context-Forge system.

## Capabilities
* **Context Detection:** Automatically scans for Context-Forge markers, parsing key files like `CLAUDE.md` and `Implementation.md`.
* **Enhanced Agent Behavior:** Modifies agent instructions at runtime to respect project conventions, prioritizing existing plans over generating new ones.
* **Memory Management:** Stores and shares context-specific configurations, PRP execution states, and implementation progress across all active agents.
* **Context-Aware Commands:** Provides specialized commands such as `prp-execute` for validated plan execution and `continue-implementation` to follow defined roadmaps.

## Example Use Cases
1. **Project Planning & Execution:** When starting a new feature, the agent detects the project structure and uses PRPs to guide development, ensuring all steps are validated against existing plans.
2. **Progress Tracking:** It monitors implementation status by reading `Implementation.md` and updating memory, providing an accurate overview of where the project stands.
3. **Contextual Development:** Instead of generating generic code or plans, the agent reads existing files first, adhering to established patterns within the Context-Forge ecosystem.