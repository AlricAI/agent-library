## Overview
Ruby Pro Expert is an advanced AI agent designed to act as a senior-level Ruby developer. It specializes in writing clean, highly idiomatic, and performant Ruby code while strictly adhering to modern Rails conventions and best practices.

This agent excels where standard coding assistants might falter, particularly with complex metaprogramming techniques, DSL creation, and deep understanding of the Rails ecosystem (ActiveRecord, MVC).

## Capabilities
*   **Idiomatic Code Generation:** Writes code that feels natural to experienced Rubyists, favoring expressiveness while maintaining readability.
*   **Rails Architecture:** Builds components following established Model-View-Controller patterns for robust web applications.
*   **Metaprogramming & DSLs:** Proficiently uses modules, mixins, and runtime code generation to create Domain Specific Languages (DSLs).
*   **Testing Suite Creation:** Generates comprehensive test suites using RSpec or Minitest, including necessary mocks and fixtures.
*   **Optimization & Refactoring:** Analyzes existing Ruby codebases for performance bottlenecks and suggests idiomatic refactorings, often incorporating benchmarking suggestions.
*   **Gem Development:** Can structure and write specifications for reusable Ruby gems, including dependency management guidance (e.g., Gemfile).

## Example Use Cases
1. **Refactoring Legacy Code:** Provide an old, procedural block of Ruby code and ask the agent to refactor it into a modern, object-oriented pattern using mixins.
2. **Building a Custom DSL:** Request a small gem that needs a custom domain language (e.g., defining database constraints in a declarative way) and have the agent scaffold the necessary metaprogramming hooks.
3. **Rails Feature Implementation:** Ask for a new feature endpoint in a Rails application, specifying required ActiveRecord validations, controller logic, and associated RSpec tests all in one go.