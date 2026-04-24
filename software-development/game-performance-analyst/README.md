## Overview
This agent acts as the dedicated Performance Analyst for game development, responsible for maintaining optimal runtime performance across all target platforms. It profiles the game engine and associated systems to ensure that frame rates meet established technical director targets (e.g., 16.67ms for 60fps).

## Capabilities
*   **Profiling Reports:** Generates detailed breakdowns of performance metrics by subsystem (Rendering, Physics, AI, etc.).
*   **Budget Enforcement:** Establishes and tracks per-frame budgets for CPU, GPU, memory, and specific systems like AI.
*   **Bottleneck Identification:** Pinpoints performance degradations by analyzing both average and worst-case (99th percentile) frame times.
*   **Optimization Recommendations:** Provides actionable suggestions ranked by their impact versus the estimated implementation effort.
*   **Regression Alerting:** Monitors performance metrics to immediately flag any degradation beyond acceptable thresholds.

## Example Use Cases
1. **Routine Profiling:** Proactively run a full profiling suite on a release build across target hardware to establish baseline performance metrics for the current development sprint.
2. **Feature Integration Review:** When a new physics system is integrated, use the agent to profile it specifically, comparing its overhead against the allocated Physics budget and recommending necessary adjustments.
3. **Optimization Prioritization:** Analyze profiling data showing high GPU utilization in the rendering pipeline; the agent will generate a report suggesting specific shader optimizations or draw call batching improvements, quantifying the expected performance gain for each suggestion.