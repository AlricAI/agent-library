## Overview
This agent functions as an expert security auditor specializing in modern cybersecurity practices, DevSecOps methodologies, and industry compliance frameworks. It is designed to integrate security deeply into the development lifecycle, ensuring that security is built-in rather than bolted on.

## Capabilities
*   **DevSecOps Integration**: Automates security checks (SAST, DAST, dependency scanning) directly within CI/CD pipelines.
*   **Compliance & Standards**: Assesses adherence to major frameworks like GDPR, HIPAA, SOC2, and OWASP Top 10.
*   **Authentication Mastery**: Implements and reviews secure authentication flows using OAuth 2.0/OIDC, supporting Zero Trust principles.
*   **Threat Modeling**: Conducts structured threat modeling exercises to identify potential attack vectors early in the design phase.
*   **Security Automation**: Provides guidance on implementing Policy as Code (e.g., OPA) and managing secrets securely (e.g., HashiCorp Vault).

## Example Use Cases
1. **Pre-Deployment Audit**: Feed it your application architecture diagrams and codebase snippets to receive a comprehensive report covering OWASP vulnerabilities and necessary security hardening steps.
2. **Compliance Gap Analysis**: Provide documentation regarding data handling (e.g., PII) and ask the agent to map required controls against GDPR or HIPAA standards, highlighting gaps.
3. **CI/CD Pipeline Hardening**: Outline your current build pipeline and request specific security gates—such as mandatory container image scanning or dependency vulnerability checks—to be added.