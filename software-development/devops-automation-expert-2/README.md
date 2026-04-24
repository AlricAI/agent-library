## Overview
This expert agent simulates a senior DevOps engineer, specializing in bridging the gap between development and operations. Its core function is to automate, stabilize, and scale software infrastructure by implementing best practices across the entire delivery pipeline.

It focuses on achieving high levels of automation (e.g., 100% IaC coverage) while ensuring systems meet stringent reliability targets like 99.9% uptime.

## Capabilities
*   **Infrastructure as Code (IaC):** Designs and implements infrastructure using tools like Terraform, Ansible, and CloudFormation for repeatable environments.
*   **Container Orchestration:** Manages complex deployments on Kubernetes, including Helm chart creation, service mesh setup, and image optimization.
*   **CI/CD Pipeline Design:** Builds end-to-end pipelines incorporating build optimization, automated testing (targeting >80% coverage), quality gates, and safe rollback procedures.
*   **Observability Implementation:** Sets up comprehensive monitoring stacks covering metrics collection, log aggregation, distributed tracing, and defining clear SLIs/SLOs.
*   **Process Improvement:** Analyzes existing workflows to identify bottlenecks, manual steps, and collaboration gaps for targeted automation solutions.

## Example Use Cases
*   **Migrating Legacy Deployments:** Analyze a set of manually deployed services and generate the necessary Terraform modules and CI/CD pipelines to achieve fully automated, version-controlled deployments on AWS.
*   **Implementing Observability:** Given existing application logs and metrics endpoints, design and scaffold the configuration for Prometheus/Grafana stack, including alert definitions and dashboard structure.
*   **Containerizing an Application:** Take a sample microservice codebase and generate optimized Dockerfiles, Kubernetes manifests (using Helm), and suggest necessary service mesh configurations.