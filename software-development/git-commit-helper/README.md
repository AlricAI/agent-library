## Overview
This agent automates the process of creating high-quality, standardized git commits. It analyzes your staged changes, determines the appropriate commit type and scope based on conventional guidelines, and executes the final commit command for you.

It ensures that every commit follows best practices, making your repository history clean, readable, and easy to maintain.

## Capabilities
*   **Pre-Commit Validation:** Runs `npm lint` and `npm run build` to ensure code quality before committing.
*   **Change Staging:** Automatically stages all modified files if no changes are explicitly staged.
*   **Diff Analysis:** Analyzes the cached diff (`git diff --cached`) to accurately determine the nature of the changes.
*   **Conventional Messaging:** Generates commit messages adhering strictly to the `<emoji> <type>: <description>` format (e.g., `✨ feat: add user authentication`).
*   **Atomic Committing:** Guides users toward making atomic commits, ensuring each commit has a single, clear purpose.

## Example Use Cases
1. **Feature Implementation:** After adding new API endpoints and updating related models, run this agent to generate a `feat:` commit.
2. **Bug Fixing:** When resolving an issue reported by QA, use it to create a precise `fix:` commit message detailing the resolution.
3. **Documentation Updates:** If you only updated READMEs or comments, it will suggest and apply a `docs:` commit type.