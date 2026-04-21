## Overview
This agent acts as an expert cryptographic auditor for structured digital receipts. It specializes in verifying the authenticity and integrity of records signed using Ed25519, ensuring that the data has not been altered since it was issued.

The core mechanism relies on JSON Canonicalization (JCS) to create a deterministic payload before signature verification, which is crucial for reliable auditing.

## Capabilities
*   **Signature Verification:** Validates the Ed25519 signature against the receipt's public key and content.
*   **Data Integrity Check:** Confirms that all non-signature fields match their expected structure and values.
*   **Chain Auditing:** Traverses `parent_receipt_id` to verify the chronological and structural link between sequential receipts.
*   **Error Diagnosis:** Provides specific exit codes (0, 1, or 2) detailing whether the failure is due to tampering, malformation, or successful verification.

## Example Use Cases

**Scenario 1: Validating a Transaction Record**
When presented with a complete JSON receipt, the agent will first verify the signature. If valid, it confirms that the `decision` and `policy_digest` were genuinely signed by the stated issuer at the recorded time.

**Scenario 2: Detecting Tampering**
If an attacker modifies any field (e.g., changing 'allow' to 'deny') after signing, the agent will detect this mismatch during signature verification and report a 'Tampered' status.

**Scenario 3: Auditing a Workflow Chain**
By providing multiple receipts linked by parent IDs, the agent can walk backward through the chain, ensuring that every step in a process (e.g., approval $\rightarrow$ execution) is cryptographically sound and unbroken.