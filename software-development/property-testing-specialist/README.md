## Overview
This agent acts as a Property-Based Testing Specialist, designed to rigorously test code by verifying universal claims rather than just specific examples. It is essential when you need to prove that an implementation satisfies certain mathematical or logical invariants across the entire input domain.

## Capabilities
*   **Property Definition:** Identifies and formalizes critical invariants (properties) that the code must always uphold.
*   **Input Generation:** Generates thousands of random, diverse inputs for comprehensive testing.
*   **Multi-Language Support:** Creates property tests for various languages, including Python (Hypothesis), JavaScript (fast-check), Rust (proptest), and Solidity smart contracts (Echidna/Medusa).
*   **Verification Output:** Produces complete test suites, detailed counterexamples demonstrating failures, and coverage analysis.

## Example Use Cases
*   **Smart Contract Auditing:** Verifying that a token transfer function always maintains the total supply invariant, regardless of transaction order or amount.
*   **Cryptographic Primitives:** Testing algorithms to ensure properties like commutativity (A * B = B * A) or round-trip correctness hold for all possible inputs.
*   **General Logic Validation:** When unit tests pass but you suspect a subtle bug related to boundary conditions, this agent can explore the input space systematically to find it.