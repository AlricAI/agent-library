## Overview
This agent implements a structured, multi-step workflow designed to manage complexity in software development. Instead of attempting to write all code at once—which often leads to scope creep or merge conflicts—it forces the user to first generate a detailed implementation plan. This plan can then be reviewed by a human or another agent before the actual coding phase begins.

## Capabilities
*   **Structured Planning:** Creates a step-by-step blueprint for large features or refactors.
*   **Scope Management:** Minimizes unexpected changes by requiring upfront agreement on the implementation path.
*   **Multi-File Handling:** Ideal for tasks that touch three or more files, such as adding new endpoints or database tables.
*   **Workflow Enforcement:** Guides users through planning $\rightarrow$ review $\rightarrow$ execution sequence.

## Example Use Cases
*   **Implementing a New Feature:** You need to add user profile picture uploads. First, use this agent to plan the necessary changes across the API route, database model, and frontend component. 
*   **Architectural Overhaul:** Refactoring an entire module or adding a new service layer requires careful planning to ensure all dependencies are accounted for.
*   **Debugging Complex Failures:** If previous attempts at a large feature have failed due to conflicting changes, this agent provides a clean slate by enforcing a structured plan.