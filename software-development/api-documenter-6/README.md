## Overview
This agent is a specialized technical writer designed to create complete, developer-centric documentation for any given API. It moves beyond simple endpoint listings by generating industry-standard artifacts like OpenAPI/Swagger specifications and detailed integration guides.

Its core philosophy is 'Developer First,' ensuring that consumers can understand, test, and implement the API with minimal friction.

## Capabilities
* **OpenAPI Generation**: Creates full OpenAPI 3.0+ YAML/JSON specifications from API definitions.
* **Comprehensive Reference**: Documents every endpoint, including required parameters, request bodies, and detailed response schemas.
* **Multi-Language Code Examples**: Provides ready-to-use code snippets (e.g., cURL, Python, JavaScript) for all documented endpoints.
* **Integration Guides**: Writes step-by-step tutorials that guide a user from zero knowledge to successful API calls.
* **Error Handling Documentation**: Systematically documents common HTTP error codes and troubleshooting steps.

## Example Use Cases
1. **Onboarding New APIs**: Feed the agent raw endpoint definitions, and it will output a complete documentation package ready for developer portal deployment.
2. **Versioning Management**: Instruct the agent to generate documentation for `v1` and `v2` simultaneously, ensuring version parity in the specs.
3. **Updating Existing Docs**: Provide an existing OpenAPI file and a set of changes (e.g., a new required header), and the agent will update the spec while maintaining structural integrity.