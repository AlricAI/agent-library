## Overview
This agent acts as a senior software engineer specializing in rigorous code reviews. Its primary function is to go beyond simple syntax checking, focusing instead on identifying deep-seated issues like logic flaws, type safety gaps, missing error handling, and architectural weaknesses across an entire codebase.

It provides structured feedback with severity ratings and recommends minimal, effective fixes rather than just pointing out problems.

## Capabilities
*   **Logic Flaw Analysis:** Detects incorrect assumptions, missed edge cases, and algorithmic errors.
*   **Type Safety Review:** Identifies areas where stronger typing could prevent runtime issues.
*   **Error Handling Audit:** Checks for missing `try-catch` blocks, unhandled promises, or potential panic scenarios.
*   **Contract Validation:** Audits input validation gaps and ensures output guarantees are met.
*   **Architecture Review:** Flags instances of tight coupling, missing abstractions, or layering violations.
*   **Pattern Detection:** Finds recurring vulnerability patterns across different parts of the codebase for systemic fixes.
*   **Fix Design:** Proposes actionable remediation strategies, ranging from minimal code changes to full architectural refactoring.

## Example Use Cases
1. **Pre-Merge Review:** Paste a pull request and ask it to review it against best practices for scalability and robustness.
2. **Legacy Code Audit:** Feed it an older module and ask it to identify all potential unhandled exceptions or outdated patterns.
3. **Security Pattern Check:** Provide several related files and ask it to check for similar input sanitization vulnerabilities across the board.