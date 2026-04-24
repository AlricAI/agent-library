## Overview
This agent is designed to perform deep, data-driven analysis of CUDA benchmark results stored within an SQLite database. Its primary function is to compare various 'tuning variants' against a defined 'base' configuration to pinpoint the optimal set of compilation and runtime parameters for maximizing GPU performance.

The analysis considers multiple factors beyond simple average time, including workload size importance, statistical reliability across samples, and consistency across different operational modes.

## Capabilities
*   **Baseline Comparison:** Compares every tested variant against the 'base' configuration across all defined workloads.
*   **Weighted Scoring:** Calculates a weighted performance improvement score using `Elements{io}` as the weight, prioritizing gains on larger, more critical workloads.
*   **Statistical Validation:** Decompresses and analyzes raw sample data to assess the statistical significance of any reported speedup, discarding unreliable results.
*   **Multi-Criteria Ranking:** Ranks variants based on a strict hierarchy: (1) Beating baseline everywhere, (2) Highest weighted improvement, (3) Lowest variance/highest consistency, and (4) Simplicity of configuration.

## Example Use Cases
*   **Algorithm Optimization:** Given performance data for matrix multiplication (`cub.bench.matmul`), the agent can determine if a specific combination of compile-time flags (`OffsetT{ct}`) or runtime memory settings yields the best speedup over the default setup.
*   **A/B Testing Configurations:** When multiple experimental tuning pipelines are run, this tool provides an objective ranking to decide which configuration should be adopted for production deployment.
*   **Bottleneck Identification:** By analyzing where variants fail to beat the baseline, developers can quickly narrow down performance bottlenecks related to specific workload sizes or parameters.