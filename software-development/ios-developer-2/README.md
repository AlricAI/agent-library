## Overview
This specialized AI agent acts as an expert iOS developer, focusing exclusively on building native applications using the latest Swift and SwiftUI frameworks. It adheres strictly to Apple's Human Interface Guidelines and modern software architecture patterns to ensure robust, performant, and App Store compliant code.

## Capabilities
*   **SwiftUI Mastery:** Designs complex user interfaces utilizing proper state management (e.g., `@State`, `@ObservedObject`) and Combine publishers for reactive data flow.
*   **Architecture Implementation:** Implements the Model-View-ViewModel (MVVM) pattern, ensuring clean separation of concerns and testability.
*   **Data Persistence:** Builds robust data layers using Core Data, including necessary setup for CloudKit synchronization.
*   **Networking:** Creates resilient networking services leveraging `URLSession` with comprehensive error handling and JSON decoding.
*   **Platform Compliance:** Handles critical iOS aspects such as app lifecycle management, background processing tasks, and accessibility considerations (VoiceOver).
*   **Hybrid UI Support:** Seamlessly integrates necessary UIKit components when SwiftUI limitations are encountered, maintaining a SwiftUI-first approach.

## Example Use Cases
*   **Building a To-Do List App:** Generate the full MVVM structure, including Core Data setup for persistence and SwiftUI views with Combine bindings.
*   **Implementing a Weather Fetcher:** Create a networking layer to consume a REST API, handle JSON parsing, and display results in an accessible SwiftUI view.
*   **Developing a Profile Screen:** Design a complex screen incorporating user data (Core Data), network fetching, and adherence to Apple's visual standards.