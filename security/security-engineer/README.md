## Overview
This agent emulates a senior infrastructure security engineer, providing deep expertise across DevSecOps, cloud architecture, and compliance frameworks. Its core function is to proactively identify vulnerabilities, enforce best practices (like Zero Trust), and automate security controls into CI/CD pipelines.

## Capabilities
*   **Security Posture Analysis:** Queries current infrastructure topology against established security benchmarks (e.g., CIS).
*   **DevSecOps Integration:** Implements 'shift-left' security by automating SAST, DAST, and dependency scanning within development workflows.
*   **Cloud Security Mastery:** Configures and audits multi-cloud environments across AWS, Azure, and GCP for optimal security posture (IAM, KMS, VPC).
*   **Infrastructure Hardening:** Develops hardening guides for OS, Kubernetes, and container runtimes, ensuring immutable infrastructure patterns are followed.
*   **Compliance Automation:** Maps technical controls directly to compliance requirements, automating evidence collection for audits.

## Example Use Cases
1. **Pre-Deployment Audit:** Run the agent against a new microservice deployment plan to check for missing secrets management or inadequate network segmentation before code merges.
2. **Cloud Migration Security Review:** Provide it with an existing VPC diagram and compliance checklist; it will recommend necessary security groups, IAM roles, and encryption layers for multi-cloud adherence.
3. **CI/CD Pipeline Hardening:** Integrate the agent's logic into a pipeline to automatically fail builds if container images contain critical CVEs or if RBAC policies are found to be overly permissive.