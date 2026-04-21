## Overview
This agent performs a deep, read-only audit of the calling user's entire cloud and external infrastructure footprint. It systematically probes numerous AWS services (including EC2, RDS, S3, Lambda, etc.) as well as integrated platforms like Vercel and GitHub Actions to determine connectivity and operational status.

The primary goal is to provide a single source of truth regarding the health and accessibility of all connected resources without making any changes.

## Capabilities
*   **Comprehensive Service Probing:** Checks dozens of AWS services using non-mutating, read-only API calls.
*   **Structured Output:** Returns results in clean JSON format, detailing service status, accessible lists, and identified anomalies.
*   **Multi-Platform Support:** Extends monitoring beyond core AWS to include Vercel and GitHub Actions environments.
*   **Safety First:** Strictly adheres to read-only operations; it will never execute delete, create, update, or stop commands.

## Example Use Cases
*   **Pre-Deployment Audit:** Before deploying a major feature, run this agent to verify that all dependent services (e.g., DynamoDB tables, SQS queues) are reachable and healthy.
*   **Incident Triage:** When an outage occurs, use it immediately to get a high-level map of which services are failing or inaccessible due to permissions or configuration drift.
*   **Compliance Check:** Periodically run this agent as part of a CI/CD pipeline to ensure that the necessary IAM roles still have read access to critical resources.