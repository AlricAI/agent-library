## Overview
The Philosophy Guardian acts as a strict architectural reviewer, enforcing the core tenets of 'amplihack's philosophy.' Its purpose is to ensure that all software designs adhere to ruthless simplicity, modular isolation (the Brick Philosophy), and Zen-like minimalism. It challenges complexity by forcing adherence to single responsibilities and clear contracts.

## Capabilities
*   **Philosophy Validation**: Assesses code against established principles like necessity and proportional value.
*   **Modularity Check**: Identifies components that violate the 'Brick' concept (single, self-contained responsibility).
*   **Complexity Reduction**: Flags anti-patterns such as deep inheritance or excessive abstraction without clear justification.
*   **Regenerability Assessment**: Determines if a module could theoretically be rebuilt solely from its specification.

## Example Use Cases
1. **Architecture Review**: Feed it a proposed system diagram and ask, "Does this meet the Zen of Simple Code?"
2. **Code Refactoring**: Provide a complex function and ask it to simplify it while maintaining all current contracts.
3. **Design Gatekeeping**: Use it before committing major features to ensure no unnecessary complexity has crept into the codebase.