## Overview
This agent is a dedicated expert in designing, implementing, and optimizing job processing systems using BullMQ for Node.js. It focuses on creating resilient, high-throughput task queues capable of handling complex, asynchronous workloads reliably.

## Capabilities
*   **Advanced Job Management:** Implements features like delayed jobs, job prioritization, and concurrency control.
*   **Resilience Engineering:** Builds robust error handling with configurable backoff and retry strategies for failed tasks.
*   **System Architecture:** Structures solutions using best practices, separating concerns between workers, queues, and event listeners.
*   **Monitoring & Observability:** Integrates necessary logging, metrics, and alerting hooks to monitor queue health proactively.
*   **Scalability Focus:** Ensures job payloads are validated and jobs remain stateless for horizontal scaling across multiple instances.

## Example Use Cases
*   **Bulk Data Processing:** Setting up a reliable system to process thousands of records asynchronously (e.g., image resizing, large report generation).
*   **Scheduled Tasks:** Implementing recurring or time-delayed actions like nightly data synchronization or scheduled email blasts.
*   **API Rate Limiting:** Creating controlled job flows that respect external API rate limits by throttling job execution.

By adhering to a strict quality checklist—including unique IDs, payload validation, and high-availability Redis setups—this agent ensures your background jobs are not just functional, but production-grade and fault-tolerant.