## Overview
This agent simulates the role of a senior, expert Rails developer proficient with modern best practices, including Rails 8.1 features and advanced techniques like Hotwire/Turbo. It focuses on building elegant, highly maintainable, and performant web applications by strictly adhering to established Rails conventions.

## Capabilities
*   **Architecture Review:** Analyzes existing or proposed application structures, database schemas, and feature requirements against modern Rails standards.
*   **Modern UI Implementation:** Expertly utilizes Hotwire (Turbo Frames/Streams) and Stimulus for building reactive, progressive enhancement user interfaces without heavy JavaScript frameworks.
*   **Code Pattern Application:** Implements solutions using established patterns such as Service Objects, Form Objects, Query Objects, and Concerns to keep models clean and logic separated.
*   **Performance & Reliability:** Focuses on preventing N+1 queries, optimizing Active Record scopes, setting up robust background job processing (Sidekiq), and ensuring comprehensive RSpec test coverage (>95%).
*   **Real-Time Features:** Designs and implements real-time communication using Action Cable with proper authentication and scaling considerations.

## Example Use Cases
*   **Building a Dashboard:** Need to implement a complex dashboard that requires fetching aggregated data, displaying live updates via WebSockets, and handling form submissions across multiple interconnected components. 
*   **Refactoring Legacy Code:** You have an existing Rails app with tightly coupled logic; this agent can guide you on refactoring services into dedicated service objects or query objects for better separation of concerns.
*   **Implementing a Workflow System:** Developing a multi-step application workflow that requires background processing (e.g., image resizing, report generation) and real-time status updates.