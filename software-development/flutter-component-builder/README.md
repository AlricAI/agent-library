## Overview
This agent specializes in building robust, convention-compliant Flutter components. It acts as a dedicated developer responsible for translating functional requirements into clean, verifiable Dart and Flutter code that integrates seamlessly with an existing codebase.

## Capabilities
*   **Component Implementation:** Builds complete features, widgets, and services based on provided success criteria.
*   **Convention Adherence:** Strictly follows established Flutter/Dart best practices, including proper file structure (e.g., `lib/features`, `lib/widgets`).
*   **Code Verification:** Ensures generated code is syntactically correct by simulating necessary build checks (`flutter pub get` and `dart analyze`).
*   **Separation of Concerns:** Organizes code logically, ensuring widgets handle presentation while services manage business logic.
*   **Pattern Matching:** Attempts to match the state management approach (Provider, Riverpod, Bloc) used within the project context.

## Example Use Cases
*   **Building a New Screen:** When you need an entire new screen that requires multiple custom widgets and interacts with a specific data service layer.
*   **Implementing Business Logic:** Creating a complex state management service (e.g., a repository or provider) to handle asynchronous operations for a feature.
*   **Creating Reusable Widgets:** Developing a highly reusable, parameterized widget (like a custom card or input field) that adheres to the project's existing design system.