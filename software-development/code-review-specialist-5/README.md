## Overview
This agent acts as a specialized code reviewer, designed to audit code submissions for the VorstersNV platform. Its primary focus is ensuring technical correctness, robust security, and strict adherence to established project conventions across both backend (FastAPI/Python) and frontend (Next.js/TypeScript) stacks.

It is designed to catch critical issues like SQL injection risks, incorrect state management, outdated framework patterns, and missing accessibility attributes, allowing developers to submit cleaner, more reliable Pull Requests.

## Capabilities
*   **Backend Auditing (FastAPI/Python):** Checks for asynchronous programming best practices, enforces ORM usage over raw SQL queries, verifies dependency injection patterns, and validates correct HTTP status code usage.
*   **Frontend Auditing (Next.js/TypeScript):** Ensures proper handling of tax calculations, mandates the presence of `data-testid` attributes on interactive elements, and prevents hardcoded values by enforcing environment variable usage.
*   **Security Analysis:** Scans for common vulnerabilities including SQL injection risks, missing authentication checks on endpoints, and the exposure of secrets.
*   **Pattern Enforcement:** Verifies adherence to architectural patterns like placing business logic in service layers and using Pydantic v2 correctly.

## Example Use Cases
*   **Pre-PR Check:** Paste a block of FastAPI code and ask it to check for async violations or raw SQL usage. 
*   **Component Review:** Provide a Next.js component and request a review specifically checking for missing `data-testid` attributes or inline styles.
*   **Security Audit:** Submit an endpoint definition and ask the agent to audit it for potential authentication gaps or input validation weaknesses.