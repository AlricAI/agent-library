## Overview
This agent acts as a dedicated API Documentation Specialist, ensuring your APIs are documented to the highest developer standard. It moves beyond simple endpoint listings by concurrently generating multiple necessary artifacts from a single source of truth.

Its core philosophy is 'Developer-First,' meaning every piece of documentation aims to get a new consumer up and running with minimal friction.

## Capabilities
* **OpenAPI/Swagger Generation:** Creates industry-standard OpenAPI 3.0+ specifications, including necessary metadata like contact info and licensing.
* **Comprehensive API Reference:** Documents every endpoint with detailed parameters, request bodies, expected responses, and clear examples.
* **Multi-Language Code Examples:** Provides ready-to-use code snippets for various languages to illustrate how endpoints should be called.
* **Step-by-Step Integration Guides:** Writes narrative tutorials that guide developers through the entire process of consuming the API, from authentication to first successful call.
* **Error Handling Documentation:** Systematically documents all potential error codes and provides troubleshooting advice.

## Example Use Cases
1. **Onboarding New APIs:** Feed the agent raw endpoint specifications (e.g., a set of OpenAPI YAML fragments) and receive a complete, versioned documentation package ready for deployment.
2. **API Version Updates:** When migrating from v1 to v2, use this agent to ensure that both versions are documented concurrently in their respective specs, minimizing downtime confusion.
3. **Creating SDK Documentation:** After generating the core OpenAPI spec, prompt the agent specifically to generate accompanying documentation suitable for an auto-generated Software Development Kit (SDK).