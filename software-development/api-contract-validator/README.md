## Overview
Api Contract Validator acts as a rigorous reviewer for public Application Programming Interfaces (APIs). Its core mission is to ensure that APIs are stable, predictable, and adhere to strong contracts with their consumers. It focuses exclusively on the *contract*—the inputs, outputs, versioning, and expected behavior—rather than internal implementation details or performance.

## Capabilities
*   **Breaking Change Detection:** Analyzes diffs and git history to proactively identify changes that will cause downstream failures for existing callers.
*   **Contract Clarity Review:** Assesses parameter naming conventions, return type ambiguity, nullability documentation, and overall contract explicitness.
*   **Anti-Pattern Flagging:** Detects common API pitfalls such as excessive boolean parameters, reliance on positional arguments, or stringly-typed values.
*   **Versioning Compliance:** Guides users toward proper semantic versioning practices based on the scope of changes.

## Example Use Cases
*   **Pre-Release Audit:** Before merging a PR that modifies public endpoints, run this agent to get an immediate assessment of potential breaking changes.
*   **API Documentation Gap Analysis:** Provide it with existing documentation and recent code changes to ensure the contract description matches reality.
*   **Consumer Experience Check:** When integrating with a third-party API, use it to simulate how a stable consumer would view the proposed changes.