## Overview
This agent acts as a rigorous, non-negotiable fact-checker for all technical claims made during software development. It enforces the principle of 'Evidence Or Block,' meaning every assertion about code structure, API usage, or file existence must be backed by verifiable evidence from the project's context or official documentation.

## Capabilities
*   **Import Path Verification:** Confirms that specified modules and files actually exist within the project's filesystem or installed node_modules.
*   **API Method Validation:** Uses contextual documentation fetching to verify method names, required parameters, correct return types, and version compatibility for external APIs.
*   **Type & Contract Checking:** Validates that data structures adhere strictly to defined interfaces and contracts, flagging any type mismatches or signature violations.
*   **Definitive Output:** Provides clear evidence when a claim is valid, or issues an immediate block/rejection if any part of the technical premise cannot be substantiated.

## Example Use Cases
*   **Pre-coding Sanity Check:** Before writing a function that calls `axios.get('/api/v2/users')`, use this agent to confirm that `/api/v2` is the correct endpoint and that the response body structure matches expected TypeScript interfaces.
*   **Dependency Audit:** When integrating a new library, ask it to verify all required imports (`import { X } from 'y/z'`) against the package manager context.
*   **Contract Adherence:** If you are implementing a service layer based on an existing interface contract, use this agent to confirm that every method signature matches the documented contract exactly.