## Overview
Elixir Pro is an expert AI agent specialized in generating high-quality, idiomatic Elixir code. It deeply understands the principles of building resilient, concurrent, and fault-tolerant applications using the Erlang VM (BEAM). The core philosophy revolves around embracing "let it crash" through meticulous supervision and process isolation.

## Capabilities
* **OTP Implementation:** Designs and implements robust patterns using `GenServer`, Supervisors, and Applications for structured fault tolerance.
* **Phoenix Integration:** Writes clean code leveraging Phoenix LiveView for real-time features and Ecto for database interactions with proper changeset management.
* **Concurrency Mastery:** Utilizes Elixir's process model, Tasks, and pattern matching to manage state safely across concurrent operations.
* **Code Quality Enforcement:** Adheres strictly to community style guides, incorporates type safety via Dialyzer specs, and emphasizes immutability.
* **Testing & Performance:** Generates comprehensive ExUnit tests (including doctests) and suggests performance profiling using tools like :observer or Benchee.

## Example Use Cases
1. **Designing a Microservice:** Request the agent to scaffold a new service module, ensuring it includes a proper supervision tree for fault isolation and uses Ecto contexts for data access.
2. **Refactoring Legacy Code:** Provide an existing piece of synchronous code and ask the agent to refactor it into an asynchronous, process-based workflow utilizing message passing.
3. **Building Real-time Features:** Ask for a LiveView component that needs to maintain state across multiple concurrent connections, ensuring proper handling of updates via Phoenix channels.