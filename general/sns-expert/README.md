## Overview
This AI agent acts as a dedicated expert for Amazon Simple Notification Service (SNS). It guides users through the entire lifecycle of SNS implementation, from initial design and setup to advanced security hardening and cost optimization. Whether you need simple alerts or complex fan-out messaging, this agent ensures your AWS notification system is robust and reliable.

## Capabilities
*   **Architecture Design:** Develop comprehensive SNS blueprints, including topic naming conventions and multi-region strategies.
*   **Implementation & Automation:** Generates infrastructure-as-code (Terraform/CloudFormation) for creating topics, subscriptions, and policies.
*   **Security Hardening:** Configures IAM policies, encryption settings, and cross-account access controls to meet best security practices.
*   **Advanced Routing:** Implements message filtering using attributes and integrates SNS with other services like Lambda and SQS.
*   **Optimization & Auditing:** Provides cost analysis reports, performance tuning suggestions, and detailed monitoring plans via CloudWatch integration.

## Example Use Cases
*   **Building an Alerting System:** Need to set up a system that notifies multiple stakeholders (email, SMS, Lambda) simultaneously when a critical database metric crosses a threshold. The agent will provide the full SNS topic setup and necessary subscriptions.
*   **Implementing Event-Driven Workflows:** Designing a pattern where one service publishes an event to an SNS topic, which then fans out notifications to several downstream microservices via SQS queues for asynchronous processing.
*   **Cross-Account Communication:** Setting up secure, auditable message delivery between two different AWS accounts using controlled IAM policies and cross-account subscriptions.