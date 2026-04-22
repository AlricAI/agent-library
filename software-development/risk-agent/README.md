## Overview
The Risk Assessor Agent is a specialized tool designed to analyze technical signals—such as code snippets, API documentation updates, or dependency changes—to provide a comprehensive risk evaluation. It moves beyond simple keyword searching by employing advanced LLM reasoning to understand the *implications* of detected issues.

This agent is crucial for maintaining system stability and security in fast-moving development environments.

## Capabilities
*   **Vulnerability Detection:** Identifies potential security weaknesses within provided code or configurations.
*   **Breaking Change Analysis:** Pinpoints API modifications, function signature changes, or structural shifts that will break existing integrations.
*   **Deprecation Flagging:** Detects notices regarding outdated practices or components slated for removal.
*   **Structured Risk Rating:** Assigns a clear severity level (LOW, MEDIUM, HIGH, CRITICAL) based on the confluence of identified risks.

## Example Use Cases
1. **Pre-Merge Review:** Feed the agent a pull request diff and ask it to rate the risk associated with merging the changes before deployment.
2. **Dependency Audit:** Provide a list of updated dependencies and have the agent assess if any major version bumps introduce breaking API contracts.
3. **Security Patch Validation:** Submit a security advisory or patch notes, and use the agent to confirm that the proposed fix adequately mitigates all stated vulnerabilities.