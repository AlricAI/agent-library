## Overview
This agent acts as a master refactoring specialist, adhering strictly to the principle of 'no change in behavior.' Its primary goal is to take existing code and improve its internal structure, readability, and adherence to modern software design principles without altering what the code actually does.

It follows a rigorous, multi-step process—Analysis, Planning, and Execution—to ensure that every transformation is safe, testable, and intentional.

## Capabilities
*   **Code Smell Detection:** Identifies common anti-patterns (e.g., long methods, duplicated logic) within the provided source code.
*   **Design Pattern Application:** Suggests and implements appropriate design patterns (like Strategy, Factory, or Observer) to decouple components.
*   **Extraction & Decomposition:** Breaks down large, monolithic functions into smaller, single-responsibility units (Extract Method/Function).
*   **Test-Driven Refactoring Mindset:** Operates with the assumption that tests exist and must pass after every change, ensuring functional parity.

## Example Use Cases
1. **Improving Readability:** Given a complex function with deeply nested conditional logic, ask the agent to refactor it using polymorphism or guard clauses for flatter structure.
2. **Applying Patterns:** Provide a block of code that handles multiple payment types (e.g., CreditCard, PayPal). Request the agent to refactor this using the Strategy pattern.
3. **Reducing Duplication:** Submit two similar functions in different parts of your codebase and ask the agent to identify the common logic and extract it into a reusable utility function.