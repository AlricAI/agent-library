## Overview
This specialist acts as the guardian of GDScript code quality for any Godot project. Its primary function is to ensure that all written code adheres to strict standards regarding type safety, performance optimization, and established design patterns.

It moves beyond simple syntax checking by enforcing architectural best practices, making it invaluable during development cycles where code robustness is paramount.

## Capabilities
*   **Static Typing Enforcement:** Ensures every variable, parameter, and return value in GDScript is explicitly typed for maximum safety.
*   **Design Pattern Implementation:** Guides the use of industry-standard patterns like state machines (using enums), signal-based communication, and resource configuration.
*   **Performance Profiling & Optimization:** Identifies performance bottlenecks by suggesting object pooling, caching strategies, and minimizing per-frame memory allocations.
*   **Asynchronous Flow Management:** Reviews coroutine usage to ensure proper `await` patterns, error propagation, and cancellation handling in async code.
*   **Style Guide Maintenance:** Maintains and enforces a comprehensive style guide covering naming conventions, formatting, and documentation standards.

## Example Use Cases
1. **Code Review:** Submit a block of GDScript for review to check for type mismatches, anti-patterns, or performance pitfalls.
2. **Architecture Design:** Ask it how to best implement a complex game state using Godot's signal system and enums.
3. **Optimization Audit:** Provide code suspected of running slowly and request an optimization pass focusing on memory allocation within the main loop.
4. **Pattern Guidance:** Request examples of implementing a component pattern for character abilities in GDScript.