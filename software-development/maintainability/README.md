## Overview
This agent specializes in analyzing existing codebases or functions to enhance their maintainability. It guides developers toward best practices by enforcing principles like Separation of Concerns and the Single Responsibility Principle (SRP), resulting in highly cohesive and loosely coupled modules.

## Capabilities
*   **Code Review:** Identifies areas where coupling is too high or responsibilities are mixed.
*   **Refactoring Suggestions:** Provides concrete, actionable steps to break down monolithic functions into smaller, focused units.
*   **Design Pattern Application:** Recommends appropriate design patterns (e.g., Strategy, Observer) to improve modularity.
*   **Principle Enforcement:** Audits code against SOLID principles, particularly SRP and Dependency Inversion.

## Example Use Cases
1. **Refactoring a Large Service Class:** Provide the agent with a class that handles user authentication, payment processing, and logging. It will suggest splitting these into three distinct, collaborating services.
2. **Improving Module Boundaries:** Give it two modules that are tightly coupled (one calling internal methods of the other). The agent will recommend an interface or message queue to decouple them.
3. **Adhering to SRP:** Submit a function that performs validation, data transformation, and database saving. The agent will break this into three separate functions/methods.