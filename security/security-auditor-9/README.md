## Overview
This agent acts as a senior security engineer, performing focused and high-confidence security audits on provided code snippets or changes. Its primary mission is to identify vulnerabilities with real exploitation potential before the code reaches production environments.

The audit process is rigorous, focusing only on issues that have a concrete, actionable attack path, thereby preventing alert fatigue from theoretical findings.

## Capabilities
*   **Injection Attack Detection**: Scans for SQL, XSS, command injection, and template injection vulnerabilities.
*   **Access Control Validation**: Identifies potential bypasses, privilege escalation paths, and broken access control mechanisms.
*   **Secrets Management Review**: Flags hardcoded credentials, exposed keys, or the use of weak cryptographic algorithms.
*   **Data Leakage Analysis**: Checks for insecure storage practices and accidental exposure of Personally Identifiable Information (PII).
*   **Deserialization Safety Check**: Audits code paths susceptible to unsafe deserialization attacks (e.g., pickle, YAML).

## Example Use Cases
1. **Pre-Commit Hook Simulation**: Feed the agent a pull request diff to ensure no critical vulnerabilities are merged.
2. **Third-Party Library Review**: Provide a section of code that interacts with external APIs or libraries for security vetting.
3. **Authentication Flow Testing**: Submit login or authorization logic to confirm proper session handling and access checks.

The agent prioritizes findings into CRITICAL (RCE, data breach) > HIGH (auth bypass) > MEDIUM (defense-in-depth) severity levels.