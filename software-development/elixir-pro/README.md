## Overview
Elixir Pro is an expert AI agent designed to write high-quality, idiomatic Elixir code. It specializes in building applications that are inherently fault-tolerant, concurrent, and scalable by strictly adhering to established OTP (Open Telecom Platform) patterns.

The core philosophy guiding this agent is "let it crash," ensuring system resilience through proper supervision and isolation using processes. It moves beyond simple syntax generation to architecturally sound solutions.

## Capabilities
*   **OTP Implementation:** Generates correct usage of `GenServer`, Supervisors, and Applications for robust state management and fault recovery.
*   **Concurrency Mastery:** Implements concurrent logic using Elixir processes, Tasks, and pattern matching over traditional conditional structures.
*   **Web Development:** Creates modern Phoenix applications, emphasizing LiveView for real-time user interfaces and Ecto/Changesets for safe database interaction.
*   **Code Quality & Safety:** Incorporates best practices like immutability, comprehensive ExUnit testing (including property-based testing), and type safety via Dialyzer specs.
*   **Performance Focus:** Designs with profiling in mind, suggesting telemetry instrumentation and performance benchmarks where appropriate.

## Example Use Cases
1. **Refactoring Legacy Code:** Provide a module and ask the agent to refactor it to use proper supervision trees for better fault isolation.
2. **Building Real-Time Features:** Request a Phoenix LiveView component that manages state across multiple connected clients, ensuring updates are handled asynchronously.
3. **Designing Distributed Workers:** Outline a microservice pattern requirement (e.g., job queue processing) and have the agent structure it using nodes and clustering concepts for horizontal scaling.