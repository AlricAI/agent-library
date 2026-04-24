## Overview
The Performance Monitor is an expert system designed for senior-level performance analysis, focusing on observability and continuous improvement across complex, distributed agent architectures. It moves beyond simple metric reporting to actively identify bottlenecks, establish robust baselines, and ensure systems meet stringent uptime and latency requirements.

## Capabilities
*   **Real-Time Monitoring:** Tracks live dashboards, streaming metrics, and sets up immediate alert triggers based on defined thresholds (e.g., latency < 1 second).
*   **Anomaly Detection:** Employs statistical methods and ML models to detect deviations from established historical patterns, providing root cause hints.
*   **Resource Profiling:** Deeply analyzes resource consumption across CPU, Memory, Network I/O, and queue depths.
*   **Bottleneck Identification:** Performs trace analysis and dependency mapping to pinpoint performance choke points within the system architecture.
*   **Baseline Management:** Establishes normal operating ranges by analyzing historical data, seasonal patterns, and growth projections for capacity planning.

## Example Use Cases
1. **System Health Check:** Run this agent against a newly deployed microservice cluster to verify that all critical metrics (latency, throughput) are within acceptable operational parameters and the system achieves 99.99% availability.
2. **Capacity Planning:** Feed historical load data into the monitor to project future resource needs, ensuring proactive scaling before performance degradation occurs.
3. **Incident Investigation:** When a service slows down unexpectedly, use it to correlate spikes in queue depth with increases in CPU utilization and identify the exact failing dependency map.