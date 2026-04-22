# Ops Automation Analysis 2026

> Date: 2026-03-21

Purpose: inventory the human-judgment-heavy operational work implied by `Blueprint-WebApp`, then identify what should be automated n

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Ops Automation Analysis 2026

Date: 2026-03-21

Purpose: inventory the human-judgment-heavy operational work implied by `Blueprint-WebApp`, then identify what should be automated now, what should remain human-in-the-loop, and what is not yet worth automating.

This document is repo-specific. It is based on the current codebase plus current official platform capabilities from OpenAI, Anthropic, Zapier, Stripe, Notion, and MCP documentation.

## Executive Summary

Blueprint has enough structured operational surface area to run much leaner than a traditional services-heavy team, but only if operations are treated as queues with explicit machine-readable state.

The highest-leverage automation opportunities in this repo are:

1. Capturer recruiting and beta routing
2. Buyer intake triage and qualification drafting
3. Site scheduling, reminder, and handoff workflows
4. Capture QA, recapture recommendation, and payout recommendation routing
5. Preview / world-model generation orchestration
6. Finance and payout exception handling
7. Support intake classification and routing

The broad rule for 2026:

- LLMs are strong enough to own triage, summarization, drafting, record enrichment, queue routing, and low-risk workflow execution.
- LLMs should still not have unsupervised authority over payouts, contract/rights signoff, irreversible billing actions, or policy-sensitive approval decisions.
- Browser/computer-use agents are now practical for legacy/internal tools, but should be a fallback behind APIs, MCP servers, and first-party integrations.

## Current Service Areas

The repo currently implies six distinct service areas:

1. Capturer supply
2. Buyer / site-operator intake
3. Site qualification and readiness review
4. World-model / preview production
5. Marketplace / buyer delivery and entitlements
6. Finance, payout, compliance, and support

## Human Ops Inventory

### 1. Capturer Recruitment, Waitlist, and Beta Activation

Current signals in repo:

- `client/src/pages/

*[truncated — see source for full prompt]*