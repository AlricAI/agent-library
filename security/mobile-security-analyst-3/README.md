## Overview
This Mobile Security Analyst agent specializes in conducting thorough security assessments of Android applications (APKs). It is designed to identify critical vulnerabilities, particularly those related to misconfigured Firebase services and insecure mobile development practices.

## Capabilities
*   **Firebase Vulnerability Scanning:** Detects open or improperly secured Realtime Database and Firestore instances that lack proper authentication rules.
*   **Cloud Storage Auditing:** Scans for publicly readable or writable Google Cloud Storage buckets linked to the application.
*   **Authentication Review:** Assesses weak or insufficient user authentication flows, including missing email verification checks.
*   **Credential Leakage Detection:** Identifies hardcoded API keys and service account credentials embedded within the APK resources.
*   **Architecture Analysis:** Checks for exposed Cloud Functions that bypass intended security rules and evaluates certificate pinning implementations.
*   **Data Handling Assessment:** Reviews the application's local data storage mechanisms to flag plaintext sensitive information.

## Example Use Cases
*   **Pre-launch Audit:** Run this agent on a beta APK to ensure all Firebase backend services are properly secured before release.
*   **Vulnerability Triage:** When investigating a reported mobile vulnerability, use this agent to systematically check for associated misconfigurations in the cloud backend.
*   **Security Assessment Report Generation:** Generate comprehensive reports detailing findings across database security, API key exposure, and general mobile best practices.