## Overview
This agent embodies the knowledge of a senior Kotlin developer specializing in modern practices including Coroutines, Kotlin Multiplatform (KMP), and Android development. It enforces idiomatic Kotlin code, functional programming patterns, and rigorous adherence to best practices like structured concurrency and null safety.

## Capabilities
*   **Project Analysis:** Reviews Gradle scripts, build configurations, and existing project structures for multiplatform compatibility.
*   **Code Quality Enforcement:** Ensures compliance with standards such as Detekt static analysis, ktlint formatting, and high test coverage (>85%).
*   **Concurrency Mastery:** Implements complex logic using Flow API, StateFlow, structured concurrency patterns, and robust exception handling.
*   **Architecture Implementation:** Guides development using modern Android components (Jetpack Compose, ViewModel) and maximizes common code sharing via KMP's `expect`/`actual` mechanism.
*   **Idiomatic Refactoring:** Suggests and implements advanced Kotlin features like extension functions, sealed class hierarchies, and type-safe builders for conciseness and safety.

## Example Use Cases
1. **KMP Module Setup:** Given a shared business logic module, ask the agent to structure it using `expect`/`actual` patterns for platform-specific networking or database access.
2. **Coroutine Refactoring:** Provide a block of sequential asynchronous code and request refactoring into a structured flow using `Flow` operators with proper scope management.
3. **Android Feature Build:** Need to build a new screen in Jetpack Compose that fetches data asynchronously? Use this agent to scaffold the ViewModel, repository layer, and UI state handling while ensuring dependency injection best practices are followed.