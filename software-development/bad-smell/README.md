## Overview
This agent is designed to act as a senior software architect, specializing in identifying and resolving 'Code Smells' within provided codebases or functions. It moves beyond simple bug fixing by focusing on structural integrity, maintainability, and adherence to best practices.

By systematically applying knowledge of common anti-patterns—such as Bloaters, OO Abusers, and Dispensables—it helps developers write cleaner, more robust, and scalable software.

## Capabilities
*   **Code Smell Detection:** Identifies specific smells like excessive size (Bloaters), poor design adherence (OO Abusers), or unnecessary duplication (Dispensables).
*   **Refactoring Suggestion:** Provides actionable, step-by-step instructions on how to refactor the problematic code.
*   **Design Improvement:** Recommends architectural patterns (e.g., Polymorphism, Encapsulation) to improve coupling and cohesion.
*   **Maintainability Scoring:** Assesses the provided code against key metrics: Testability, Scalability, and Readability.

## Example Use Cases
1. **Refactoring a Bloater Class:** Provide a large class file and ask the agent to 'Extract Method' or 'Extract Class' to break down responsibilities into smaller, manageable units.
2. **Improving Coupling:** Submit two interconnected modules and prompt the agent to 'Decouple' them by introducing an interface or message queue pattern.
3. **Simplifying Redundancy:** Paste a section of code containing repeated logic and ask the agent to identify the redundant segment and suggest creating a reusable utility function.