# SECURITY

> If you believe you've found a security issue in OpenClaw, please report it privately.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Security Policy

If you believe you've found a security issue in OpenClaw, please report it privately.

## Reporting

Report vulnerabilities directly to the repository where the issue lives:

- **Core CLI and gateway** — [openclaw/openclaw](https://github.com/openclaw/openclaw)
- **macOS desktop app** — [openclaw/openclaw](https://github.com/openclaw/openclaw) (apps/macos)
- **iOS app** — [openclaw/openclaw](https://github.com/openclaw/openclaw) (apps/ios)
- **Android app** — [openclaw/openclaw](https://github.com/openclaw/openclaw) (apps/android)
- **ClawHub** — [openclaw/clawhub](https://github.com/openclaw/clawhub)
- **Trust and threat model** — [openclaw/trust](https://github.com/openclaw/trust)

For issues that don't fit a specific repo, or if you're unsure, email **[security@openclaw.ai](mailto:security@openclaw.ai)** and we'll route it.

For full reporting instructions see our [Trust page](https://trust.openclaw.ai).

### Required in Reports

1. **Title**
2. **Severity Assessment**
3. **Impact**
4. **Affected Component**
5. **Technical Reproduction**
6. **Demonstrated Impact**
7. **Environment**
8. **Remediation Advice**

Reports without reproduction steps, demonstrated impact, and remediation advice will be deprioritized. Given the volume of AI-generated scanner findings, we must ensure we're receiving vetted reports from researchers who understand the issues.

### Report Acceptance Gate (Triage Fast Path)

For fastest triage, include all of the following:

- Exact vulnerable path (`file`, function, and line range) on a current revision.
- Tested version details (OpenClaw version and/or commit SHA).
- Reproducible PoC against latest `main` or latest released version.
- If the claim targets a released version, evidence from the shipped tag and published artifact/package for that exact version (not only `main`).
- Demonstrated impact tied to OpenClaw's documented trust boundaries.
- For exposed-secret reports: proof the credential is OpenClaw-owned (or grant

*[truncated — see source for full prompt]*