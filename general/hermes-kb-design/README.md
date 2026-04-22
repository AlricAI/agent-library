# Hermes Kb Design

> ## Purpose

This repo gets a constrained Hermes knowledge base under [`knowledge/`](/Users/nijelhunt_1/workspace/Blueprint-WebApp/knowledge).

The goa

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Hermes KB Design

## Purpose

This repo gets a constrained Hermes knowledge base under [`knowledge/`](/Users/nijelhunt_1/workspace/Blueprint-WebApp/knowledge).

The goal is not to create a second company brain that competes with Paperclip, Notion, Firebase, package manifests, or capture provenance. The goal is to give Hermes-backed research and enablement agents a durable markdown workspace where useful research compounds across runs.

This design follows Blueprint's repo doctrine:

- Paperclip remains the source of truth for work state and ownership.
- Rights, privacy, approvals, pricing commitments, package/runtime truth, and capture provenance stay in their canonical systems.
- Hermes KB pages are support artifacts for research, synthesis, and reusable enablement.

## Authority Boundary

The Hermes KB is allowed to support:

- market and competitor research
- account dossiers
- sales, procurement, and support playbooks
- documentation synthesis
- founder brief background research

The Hermes KB is not allowed to become the source of truth for:

- Paperclip work state
- approvals or sign-off state
- rights or privacy decisions
- pricing or legal commitments
- capture provenance
- package manifests or hosted runtime truth

If a KB page discusses any of the forbidden categories, it must link out to the authoritative system and explicitly say that the KB page is derivative context only.

## Brain-First Lookup Protocol

Before external research on buyers, companies, competitors, cities, objections, or GTM patterns:

1. Search the existing KB first.
2. Read the most relevant compiled page before starting new web research.
3. Check `knowledge/indexes/contradictions.md` and `knowledge/indexes/stale-pages.md` when the topic may be disputed or stale.
4. Only then call external web search, APIs, or workspace tools for missing evidence.

This is a hard workflow rule, not a style preference.

If a compiled page already exists for the subject, the default action is to update

*[truncated — see source for full prompt]*