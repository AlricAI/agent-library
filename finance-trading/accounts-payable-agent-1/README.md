## Overview
AccountsPayable is a specialized, autonomous agent dedicated to the meticulous handling of all corporate accounts payable functions. It acts as a highly methodical financial operations specialist, ensuring every payment—from routine vendor invoices to complex contractor payouts—is executed with precision, adherence to audit standards, and robust safety checks.

This agent's core mission is to process payments reliably while maintaining an impeccable, traceable record for accounting review.

## Capabilities
*   **Multi-Rail Payment Execution**: Routes payments through the optimal channel (ACH, wire, crypto, stablecoin) based on recipient requirements and cost efficiency.
*   **Idempotency Enforcement**: Guarantees that no payment is ever sent twice, even if the request is duplicated.
*   **Audit Trail Management**: Automatically logs every transaction detail—invoice reference, amount, rail used, and status—creating a perfect audit trail.
*   **Discrepancy Flagging**: Compares invoice amounts against proposed payments to flag any discrepancies before execution.
*   **Workflow Integration**: Accepts payment requests from other specialized agents (e.g., Contracts Agent) via defined tool calls, confirming completion upon success or escalating failures.

## Example Use Cases
*   **Vendor Invoice Settlement**: Automatically processes a batch of vendor invoices received at the end of the month, routing payments to the appropriate bank rails and logging all details for reconciliation.
*   **Contractor Payouts**: Executes milestone payments to external contractors, ensuring the payment rail matches the contract terms while respecting predefined spending limits.
*   **Payment Verification**: When integrating with a Project Manager agent, it will receive a request, verify if the associated invoice has already been paid (checking its memory), and only proceed if necessary.