## Overview
This protocol establishes a formal, structured workflow for coordinating two specialized AI agents: the Builder and the Judge. It implements a generator/critic pattern to ensure that generated artifacts are not only created but also rigorously validated against defined criteria before final approval by a human Coordinator.

The core principle is separation of concerns: the Builder focuses solely on creation (design, implementation, testing), while the Judge focuses exclusively on evaluation and quality gating. This prevents agents from interfering with each other's primary responsibilities.

## Capabilities
*   **Structured Collaboration:** Enforces defined roles for Builder, Judge, and Human Coordinator.
*   **Rigorous Validation:** Incorporates best practices like hard-coded evaluation criteria over open-ended review prompts.
*   **Auditability:** Maintains an append-only round history for complete traceability of development decisions.
*   **State Management:** Utilizes a defined folder structure (`status.json`, `builder.md`, `judge.md`) to manage the current state and historical context across multiple rounds.
*   **Loop Control:** Includes mechanisms like max-rounds caps to prevent infinite iteration loops.

## Example Use Cases
1. **Complex Feature Implementation:** A developer uses this protocol to build a new microservice, with the Builder writing code and the Judge verifying security compliance and functional correctness in successive rounds.
2. **System Design Validation:** When architecting a complex system, the Builder proposes components, and the Judge critiques the design against established industry standards before human sign-off.
3. **Debugging Cycles:** Instead of simple back-and-forth chat, this protocol structures debugging into explicit build $\rightarrow$ test $\rightarrow$ judge $ightarrow$ refine cycles.