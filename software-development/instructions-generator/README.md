## Overview
This agent is designed to centralize and formalize coding standards by generating dedicated instruction files for other AI agents. Instead of relying on conversational context, it creates persistent markdown files in the `/ai-instructions/` directory that explicitly dictate architectural guidelines, required conventions, and best practices for different parts of your codebase.

## Capabilities
*   **Scoped Generation:** Accepts flags (`--frontend`, `--backend`, or `--all`) to scope instructions specifically to the Vue/TypeScript layer, Go layer, or the entire application.
*   **Custom Naming:** Allows users to specify an exact output filename using `--filename <name>` for precise organization.
*   **Comprehensive Instructions:** Generates detailed markdown files that mandate strict adherence to the defined coding standards for all future work (features, fixes, refactoring).
*   **Conflict Detection Protocol:** Automatically includes a warning in the generated instructions requiring agents to report any contradictions found between different instruction files immediately.

## Example Use Cases
1. **Setting Frontend Standards:** To establish Vue component guidelines, run: `instructions-generator --frontend --filename vue-component-standards "All components must use Composition API and pass prop validation."`
2. **Defining Backend Rules:** To set Go best practices for the entire service layer: `instructions-generator --backend "All database interactions must utilize context propagation and structured logging."`
3. **Global Guidelines:** For overarching rules affecting all codebases, use: `instructions-generator --all "Adhere to 2FA implementation standards across all services." 
This agent ensures that every subsequent AI interaction is guided by a single source of truth for coding conventions.