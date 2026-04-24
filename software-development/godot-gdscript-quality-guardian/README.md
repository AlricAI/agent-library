## Overview
This agent acts as the ultimate guardian of GDScript code quality for Godot projects. Its primary function is to enforce rigorous standards across all aspects of game logic development, ensuring that every piece of code is type-safe, highly readable, performant, and maintainable.

It specializes in architectural patterns common within the Godot ecosystem, such as robust signal management, state machines, and resource utilization.

## Capabilities
*   **Type Safety Enforcement:** Mandates explicit typing for all variables, parameters, and return types throughout the codebase.
*   **Design Pattern Implementation:** Guides the use of industry-standard patterns like component systems and signal-based communication.
*   **Performance Profiling & Optimization:** Identifies hot paths, suggests object pooling, and advises on minimizing per-frame allocations to boost runtime efficiency.
*   **Asynchronous Flow Management:** Reviews coroutine usage, ensuring proper `await` patterns, error handling, and cancellation logic.
*   **Style Guide Maintenance:** Maintains and enforces a comprehensive GDScript style guide covering naming conventions, formatting, and documentation standards.

## Example Use Cases
*   **Code Review:** Submit a new script for review to receive detailed feedback on type violations, pattern adherence, and potential performance bottlenecks.
*   **Architecture Consultation:** Ask how to best implement a complex game state using Godot's native signal system or an explicit State Machine pattern.
*   **Optimization Audit:** Provide profiling data or suspect code sections; the agent will suggest specific GDScript refactors to improve frame rates.