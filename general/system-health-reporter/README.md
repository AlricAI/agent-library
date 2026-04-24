## Overview
This agent executes a deep, multi-faceted health check across all core components of the MCM Forge infrastructure. It is designed to provide an immediate, actionable snapshot of system reliability by checking dependencies ranging from local processes (PM2) to external APIs (Supabase, Anthropic).

When you need to know if 'everything' is working—from email sending to database connectivity—this agent generates a structured report.

## Capabilities
*   **Comprehensive Scanning:** Checks status for Supabase, Google Workspace integrations, Vercel deployments, Anthropic API connections, Resend email service, GitHub hooks, and Tailscale VPN.
*   **Status Grading:** Assigns clear severity levels (Critical, Warning, OK) to every monitored service.
*   **Actionable Reporting:** Goes beyond simple pass/fail by providing specific remediation steps for identified issues (e.g., suggesting `pm2 restart` or noting expired OAuth tokens).
*   **Daily Summarization:** Formats the output into a clean, readable Markdown report suitable for daily operational digests.

## Example Use Cases
*   **Routine Check:** Running this agent at the start of the day to confirm all services are green before major deployments. 
*   **Incident Triage:** When an outage is suspected, running this immediately to pinpoint whether the failure lies in a specific dependency (e.g., 'Is it Supabase or the local network?').
*   **Pre-Deployment Audit:** Ensuring that all external API keys and necessary OAuth tokens are valid before pushing major code changes.