## Overview
Forge is not intended to be a general AI coding toolbox. Instead, it functions as a deterministic harness operating system designed specifically for engineering teams tackling long-lived build and repair tasks that span multiple sessions, hosts, or interruptions. Its core philosophy centers on strengthening the foundational guarantees of complex software workflows.

## Capabilities
*   **Determinism Focus:** Prioritizes making runtime decisions highly predictable across different execution environments.
*   **Verifiability & Reproducibility:** Explicitly enhances verification paths to ensure results can be traced and repeated reliably.
*   **Recoverability:** Structures work to make failure recovery straightforward, even after significant interruptions.
*   **Observability:** Creates robust audit trails and shared control planes for deep insight into the build process.
*   **Degraded State Handling:** Explicitly models and manages how the system behaves when components or hosts fail (the 'degraded-host story').

## Example Use Cases
1. **Complex CI/CD Pipelines:** Managing multi-stage deployments where state must be perfectly preserved across different build agents.
2. **Large-Scale System Repair:** Working on legacy codebases or distributed systems that require iterative, verifiable fixes over weeks of development time.
3. **Academic Research Workflows:** Running computationally intensive simulations where the exact sequence and environment setup are paramount to scientific validity.

Use Forge when your primary concern is not just *getting* the answer, but proving *how* you got it, ensuring that every step taken is auditable and recoverable.