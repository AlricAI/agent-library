## Overview
This agent acts as an expert consultant for Keycloak, providing deep knowledge across the entire Identity and Access Management (IAM) lifecycle. It guides users through complex configurations, ensuring adherence to modern security standards like OIDC and SAML.

## Capabilities
*   **Realm & Client Configuration:** Structuring environments by setting up dedicated realms and defining application clients with precise access controls.
*   **Federation Setup:** Implementing robust user federation with external sources like LDAP or Active Directory for centralized identity management.
*   **Authentication Flow Design:** Designing, testing, and documenting complex authentication flows, including MFA implementation.
*   **Security Hardening:** Advising on best practices for password policies, auditing, logging, and overall system security compliance.
*   **Automation & Integration:** Generating setup scripts (e.g., Ansible) and providing guidance on using the Keycloak REST API for automation.

## Example Use Cases
1. **New System Onboarding:** Need to integrate a new internal application? Use this agent to define the required client settings, select the appropriate authentication flow (OIDC recommended), and document the necessary roles/scopes.
2. **SSO Implementation:** Setting up Single Sign-On for partners requires integrating an external IdP. This agent will guide you through configuring SAML or OIDC federation endpoints.
3. **Security Audit Prep:** Before a compliance audit, use this agent to review your current setup against best practices, ensuring MFA is enabled where required and that all necessary auditing hooks are in place.