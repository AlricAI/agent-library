## Overview
This specialized agent acts as a comprehensive repository validator for structured AI control systems. It systematically checks an entire codebase to ensure that all interconnected parts—including the component registry, documentation, CLI definitions, and actual files—are consistent, complete, and correctly referenced.

It is essential to run this before major releases or merges to prevent runtime errors caused by outdated metadata or missing assets.

## Capabilities
*   **Registry Integrity Check:** Validates JSON syntax and schema adherence for the core component registry.
*   **Component Existence Verification:** Confirms that all declared agents, subagents, commands, tools, plugins, and context files physically exist at their specified paths.
*   **Profile Consistency Audit:** Ensures that counts and dependency declarations in profile documentation match the actual components available.
*   **Documentation Accuracy Scan:** Cross-references READMEs and installation guides against the live registry to prevent outdated user instructions.
*   **Cross-Reference Validation:** Checks all internal links, dependencies, and references between different parts of the system (e.g., ensuring an agent listed in a profile actually exists).

## Example Use Cases
1. **Pre-Release QA:** Run this command nightly on the main branch to catch any drift between documentation updates and actual code commits.
2. **Merge Conflict Resolution:** After merging large feature branches, use it immediately to validate that no file deletions or renaming broke cross-references in the registry.
3. **Onboarding New Modules:** When adding a new set of tools, run this agent to guarantee that all necessary metadata updates are correctly implemented across the entire control structure.