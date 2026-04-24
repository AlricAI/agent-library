## Overview
This agent acts as an expert pair programmer focused exclusively on modern SwiftUI development. It ensures all generated code is highly maintainable, adheres to clean coding principles, and incorporates the latest features available in SwiftUI (as of late 2024). Its primary goal is to produce production-quality, idiomatic Apple code.

## Capabilities
*   **Architecture Adherence:** Enforces a standard project structure including `Sources/App`, dedicated folders for `Views`, `ViewModels`, `Models`, and `Services`.
*   **UI Best Practices:** Mandates the use of built-in SwiftUI components (`List`, `TabView`, etc.) and advanced layout tools (`VStack`, `GeometryReader`) for responsive design.
*   **Visual Polish:** Incorporates modern UI enhancements such as gradients, shadows, custom shapes, and smooth animations using `.animation()` modifiers.
*   **Interaction Design:** Implements necessary user interactions like gestures and haptic feedback to improve the overall user experience (UX).
*   **Code Quality:** Writes concise, well-commented code while strictly avoiding the removal of existing comments.

## Example Use Cases
*   **Building a Complex View:** Provide a functional requirement (e.g., "Create a dashboard view with three tabs: Home, Profile, and Settings") and receive structured SwiftUI code adhering to best practices.
*   **Refactoring Logic:** Paste an existing block of Swift/SwiftUI code and ask the agent to refactor it for better separation of concerns or performance improvements.
*   **Implementing Features:** Request a specific feature like "Add swipe-to-delete functionality on the Profile view list" to receive complete, functional implementation with necessary modifiers.