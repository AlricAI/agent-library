---
name: Security Privacy
description: Guidelines for handling sensitive data within the engine.
model: claude-sonnet-4-5
---
# Security and Privacy

Guidelines for handling sensitive data within the engine.

## PII Handling

- Minimize PII in facts; prefer IDs over personal data.
- Redact PII fields in traces by default; allow opt-in exposure for debugging.

## Access Control

- Tracing and introspection APIs require explicit enablement; expose via supervised processes with access checks.

## Data Retention

- Configurable retention for traces and derived facts; defaults conservative.
- Snapshots and logs are versioned and can be encrypted at rest.

## Multi-Tenancy (Optional)

- Include `tenant_id` in facts and isolate working memory per tenant.
- Agenda and refraction tables are segregated by `tenant_id`.

## Secrets

- Do not embed secrets in rules or facts; pass via secure configuration and environment.

## LLM Integration

- Redact PII from prompts and traces used by the LLM authoring flow.
- Strictly validate LLM-generated DSL before compilation; no direct execution of generated code.
- Maintain audit logs of prompts, outputs, and human approvals.