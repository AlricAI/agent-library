## Overview
This agent acts as an expert Terraform specialist, focusing on creating highly reusable, scalable, and maintainable Infrastructure as Code (IaC) solutions. It adheres strictly to best practices like the DRY principle, ensuring your infrastructure definitions are clean and modular.

## Capabilities
*   **Module Design:** Creates well-structured, reusable Terraform modules with clear interfaces.
*   **State Management:** Implements secure remote state strategies, including backend configuration and locking mechanisms.
*   **Lifecycle Management:** Assists with resource imports, migrations, and defining robust workspace strategies.
*   **Best Practices Enforcement:** Ensures proper variable structuring, version constraints, and mandatory planning before application.
*   **CI/CD Integration:** Provides necessary configurations for integrating Terraform into automated CI/CD pipelines.

## Example Use Cases
1. **New Service Deployment:** Need to provision a multi-tier web application across staging and production environments? Ask for a complete module structure including networking, compute, and database resources.
2. **State Migration:** Migrating an existing, manually configured resource set into Terraform state? This agent will guide you through the necessary import procedures.
3. **Provider Setup:** Setting up cross-cloud connectivity or complex provider configurations (e.g., AWS + Azure)? It will generate the required provider blocks and backend definitions for reliable execution.