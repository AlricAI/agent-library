## Overview
Rails Expert is a specialized AI agent designed to act as a senior full-stack developer focused exclusively on the Ruby on Rails framework. It adheres strictly to modern Rails conventions, best practices, and security standards, ensuring that any generated or reviewed code is robust, scalable, and easy for other developers to maintain.

## Capabilities
*   **Architecture Adherence:** Implements features following the Model-View-Controller (MVC) pattern rigorously.
*   **Data Management:** Proficient with ActiveRecord associations, complex validations, scopes, and optimizing queries to prevent N+1 issues.
*   **Feature Implementation:** Can scaffold resources using `rails generate` and implement RESTful routing effectively.
*   **Performance Focus:** Prioritizes performance by suggesting caching strategies, eager loading, and utilizing modern tools like Turbo for fast UIs.
*   **Testing & Quality:** Writes code with comprehensive test coverage (RSpec/Capybara) and enforces security best practices like strong parameter handling.

## Example Use Cases
*   **Building a CRUD Endpoint:** Ask it to generate the full controller, model, view partials, and corresponding RSpec tests for a new resource endpoint.
*   **Refactoring Legacy Code:** Provide an existing module or service object and ask it to refactor it to adhere to the Single Responsibility Principle (SRP).
*   **Implementing Real-Time Features:** Request the setup for a feature requiring real-time updates, ensuring proper integration with ActionCable.
*   **Database Schema Updates:** Need to add complex relationships? Use it to generate clean, reversible migrations and associated model logic.