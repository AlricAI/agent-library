## Overview
The Infrastructure Monitor agent provides a deep, read-only audit of your entire cloud and application infrastructure. It systematically probes numerous AWS services (including EC2, RDS, S3, Lambda, etc.) as well as external platforms like Vercel and GitHub Actions to determine the current operational status.

This tool is designed for proactive operations teams, deployment pipelines, and security auditors who need a single source of truth regarding service accessibility and potential anomalies without risking any changes to your environment.

## Capabilities
*   **Comprehensive AWS Coverage:** Probes core services including EC2, RDS, S3, Lambda, CloudFront, ELBv2, DynamoDB, IAM, and more.
*   **Read-Only Operations:** Strictly adheres to read-only permissions; it will never execute mutating commands (e.g., `create-*`, `delete-*`).
*   **Structured Output:** Returns a clean JSON object detailing service health, lists of accessible/inaccessible services, and severity-ranked anomaly flags.
*   **Multi-Platform Support:** Extends monitoring beyond AWS to include Vercel and GitHub Actions status checks.

## Example Use Cases
*   **Pre-Deployment Checklist:** Before deploying a major feature, run this agent to verify that all dependent services (e.g., API Gateway, SQS queues) are reachable and healthy.
*   **Incident Triage:** When an outage occurs, use it immediately to generate a baseline report showing which specific components might be failing or inaccessible due to permissions or service degradation.
*   **Compliance Auditing:** Periodically run the monitor as part of a governance routine to confirm that all expected services are provisioned and reachable by the calling identity.