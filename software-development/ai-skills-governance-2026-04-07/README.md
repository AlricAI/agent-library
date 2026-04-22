# Ai Skills Governance 2026 04 07

> Date: 2026-04-07

Status: Active

Scope: Shared AI-tooling and skill-governance rules for `Blueprint-WebApp` across Claude, Codex, Hermes, and Papercl

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# AI Skills Governance

Date: 2026-04-07

Status: Active

Scope: Shared AI-tooling and skill-governance rules for `Blueprint-WebApp` across Claude, Codex, Hermes, and Paperclip-routed agent lanes.

## Applies To

This document applies to:

- repo-level Claude-guided runs
- repo-level Codex-guided runs
- Hermes-backed Paperclip agents operating in this repo
- any other agent lane that reads repo doctrine before acting in `Blueprint-WebApp`

If a repo instruction file mentions Claude specifically because of filename convention, treat the guidance as shared unless it explicitly says otherwise.

## Core Rule

Use AI tooling as a support layer on top of Blueprint's current stack.

Do not use AI tooling to implicitly choose a new architecture for the repo.

## Current Primary Stack

The current primary stack remains:

- Vite + Express + TypeScript
- Firebase client auth + Firebase Admin / Firestore
- Stripe + Stripe Connect
- Render
- Redis
- Notion
- Paperclip
- the current AI runtime and harness paths already modeled in repo code and env

No imported skill, external guide, or AI coding pattern may override this by default.

## Approved Uses

### 1. Repo Understanding

Approved:

- reading canonical repo docs
- reading code directly
- bounded use of packed-context tools such as Repomix for narrow slices, external reference repos, or cross-repo comparison
- curated provider best-practice skills for services Blueprint already uses

Not approved:

- replacing direct reading of canonical repo docs with packed exports by default
- using external starter repos as the source of truth for this repo's architecture

### 2. Implementation Support

Approved:

- code generation that fits current repo contracts
- test generation and verification support
- architecture review against current doctrine
- debugging support
- issue-scoped implementation work

Not approved:

- architecture drift driven by generic SaaS boilerplates
- adding second-auth or second-datastore patterns because a 

*[truncated — see source for full prompt]*