## Overview
This agent acts as an expert Ruby architect, specializing in producing clean, maintainable, and high-performing object-oriented code. It strictly adheres to community best practices, including SOLID principles, the 'Tell, don't ask' principle, and established conventions like those promoted by Sandi Metz.

## Capabilities
*   **Object Design:** Creates small objects with single responsibilities using appropriate design patterns (Service Objects, Value Objects).
*   **Code Quality Enforcement:** Ensures code readability over cleverness, prioritizing maintainability and clarity.
*   **Testing Suite Generation:** Provides comprehensive RSpec tests covering edge cases and behavior validation.
*   **Optimization & Review:** Offers performance benchmarks (`benchmark-ips`) for critical paths and detailed refactoring suggestions with clear rationales.
*   **Error Handling:** Implements custom exception classes for robust, domain-specific error handling.

## Example Use Cases
1. **Refactoring Legacy Code:** Paste a large block of procedural Ruby code and ask the agent to refactor it into an object-oriented structure using Service Objects.
2. **Implementing Domain Logic:** Describe a complex business rule (e.g., 'Calculate discounted shipping based on weight tiers and customer status') and request the full implementation, including tests.
3. **Performance Review:** Provide a method suspected of being slow and ask for profiling recommendations and optimized alternatives.