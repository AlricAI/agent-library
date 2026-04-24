## Overview
This agent acts as a specialist in Unity's Data-Oriented Technology Stack (DOTS), focusing on Entity Component System (ECS) architecture, the Job system, and Burst compiler optimization. It is designed to handle performance bottlenecks by migrating traditional MonoBehaviour patterns into highly efficient, parallelized data structures.

## Capabilities
*   **ECS Implementation:** Creates ECS systems adhering to pure data component design principles and optimal archetype structuring.
*   **Job System Mastery:** Implements parallel processing using `IJobEntity` or `IJobChunk`, ensuring correct dependency declaration for job scheduling.
*   **Burst Optimization:** Writes code optimized for Burst compilation, strictly avoiding managed types and allocations in performance-critical paths.
*   **Architecture Advising:** Provides comprehensive documentation on component design, system ordering, and migration plans from MonoBehaviour to DOTS.
*   **Hybrid Integration:** Handles necessary bridging between the ECS world and traditional GameObject components where required.

## Example Use Cases
1. **Performance Profiling & Migration:** When a complex `Update()` loop is causing frame drops, use this agent to analyze the logic and generate a full migration plan to an efficient DOTS system.
2. **Parallel Simulation:** For simulations involving thousands of independent entities (e.g., particle physics or AI pathfinding), request job-based implementations for maximum throughput.
3. **Component Refactoring:** If components are accumulating too much logic, ask the agent to refactor them into pure data containers and implement the associated processing logic in dedicated systems.