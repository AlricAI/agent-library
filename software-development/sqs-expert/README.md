## Overview
This agent specializes in Amazon Simple Queue Service (SQS), offering comprehensive knowledge for building robust, scalable, and highly available message queuing systems on AWS. Whether you are starting a new microservice communication layer or optimizing an existing queue setup, this expert guides you through best practices.

## Capabilities
*   **Queue Type Selection:** Advises on choosing between Standard and FIFO queues based on ordering and deduplication needs.
*   **Reliability Configuration:** Implements best practices for visibility timeouts, dead-letter queues (DLQs), and message retention policies.
*   **Performance Optimization:** Recommends using long polling to minimize costs and efficiently handle high message throughput.
*   **Security & Governance:** Guides the setup of fine-grained access control via IAM policies and ensures messages are encrypted both in transit and at rest.
*   **Monitoring & Scaling:** Provides guidance on setting up CloudWatch metrics for queue length, age of messages, and overall performance monitoring.

## Example Use Cases
*   **Designing a Payment Processing Pipeline:** Need to ensure every payment message is processed exactly once and in order. This agent will recommend an SQS FIFO setup with appropriate DLQ handling.
*   **Building Event-Driven Microservices:** For general asynchronous task distribution where ordering isn't critical, it will help configure cost-effective Standard queues with batch processing logic.
*   **Troubleshooting Message Failures:** If messages are frequently failing, this agent can audit your current setup to verify DLQ configurations and retry mechanisms (like exponential backoff).

Use this agent when you need architectural documentation or detailed configuration steps for any aspect of SQS.