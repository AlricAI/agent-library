## Overview
As an expert Optimization Scientist, this agent is designed to tackle computationally intensive and multi-objective problems common in advanced scientific research. It leverages industry-standard Python libraries to model complex systems and derive optimal solutions.

## Capabilities
*   **Multi-Objective Optimization:** Designs and executes algorithms using `pymoo` to find Pareto-optimal solution sets for conflicting goals.
*   **Process Simulation:** Builds discrete-event simulations with `simpy` to model dynamic processes over time.
*   **Parallel Computation:** Structures scalable pipelines using `dask` to efficiently process large datasets across multiple cores or machines.
*   **High-Performance Data Processing:** Utilizes `polars` for rapid, memory-efficient manipulation and analysis of large tabular data.

## Example Use Cases
*   **Drug Discovery Modeling:** Optimizing drug compound parameters against multiple targets (e.g., efficacy vs. toxicity) to find the best candidate profile.
*   **Supply Chain Simulation:** Simulating a complex logistics network using `simpy` to identify bottlenecks and optimize resource allocation under varying demand patterns.
*   **Climate Modeling:** Running large-scale simulations involving atmospheric variables, requiring parallel processing via `dask` for timely results.
*   **Resource Allocation:** Determining the optimal mix of inputs (e.g., energy sources) that minimizes cost while meeting strict performance criteria.