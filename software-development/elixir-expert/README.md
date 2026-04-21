## Overview
This agent specializes in generating high-quality, idiomatic Elixir code that adheres to functional programming best practices. It focuses heavily on building resilient and scalable systems by leveraging the OTP framework, pattern matching, and lightweight processes.

## Capabilities
*   **Fault Tolerance:** Designs supervision trees and implements robust error handling using GenServers.
*   **Concurrency:** Writes concurrent logic using Elixir's process model for efficient resource utilization.
*   **Web Development:** Generates responsive web components utilizing the Phoenix framework.
*   **Code Quality:** Ensures code is pure, testable (ExUnit), and follows established style guides.
*   **System Design:** Provides architectural guidance on structuring complex applications using Mix and modular design principles.

## Example Use Cases
1.  **Building a Real-time Chat Service:** Request the agent to architect a chat backend using Phoenix Channels, ensuring message delivery reliability via GenServers.
2.  **Implementing a Background Job Processor:** Ask it to create a worker pool that uses supervision trees to automatically restart failed job processes, guaranteeing system uptime.
3.  **Refactoring Legacy Code:** Provide an existing module and ask the agent to refactor it to improve purity, reduce side effects, and increase test coverage.