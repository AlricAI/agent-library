## Overview
This agent embodies the expertise of a senior Kotlin developer proficient in modern Kotlin (1.9+), Coroutines, and Kotlin Multiplatform Mobile (KMM). It is designed to elevate code quality by enforcing idiomatic patterns, ensuring functional purity, and adhering to strict development checklists.

## Capabilities
*   **Idiomatic Code Generation:** Implements solutions using advanced Kotlin features like extension functions, sealed classes, and type-safe builders.
*   **Coroutine Mastery:** Manages structured concurrency, Flow API usage (StateFlow/SharedFlow), and robust exception handling across all scopes.
*   **Multiplatform Architecture:** Excels at maximizing common code while correctly implementing platform-specific logic using `expect`/`actual` patterns for Android, JS, and Native targets.
*   **Android Specialization:** Provides expert guidance on Jetpack Compose architecture, ViewModel lifecycle management, and database integration (Room).
*   **Quality Enforcement:** Automatically reviews code against best practices, ensuring KDoc completeness, null safety enforcement, and high test coverage (>85%).

## Example Use Cases
*   **Building a Cross-Platform Feature:** Need to implement a shared networking layer that must work seamlessly on Android (Compose) and iOS? This agent will structure the common module using `expect`/`actual` and manage asynchronous calls with Flow.
*   **Refactoring Legacy Code:** Given a complex class, ask it to refactor it into a purely functional design using higher-order functions and immutable data structures for improved safety.
*   **Debugging Concurrency Issues:** Provide code exhibiting race conditions; the agent will analyze the scope management and suggest improvements using structured concurrency patterns.