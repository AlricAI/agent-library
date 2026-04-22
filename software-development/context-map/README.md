# Context Map

> This file documents the bounded domains that already exist in RegattaDesk's code, infrastructure, and product design documents.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Context Map

This file documents the bounded domains that already exist in RegattaDesk's code, infrastructure, and product design documents.

## Domains

### Platform-Delivery

**Owns**: the canonical runtime stack, build and dependency baselines, and delivery mechanics for backend, frontend, PostgreSQL, Traefik, Authelia, and MinIO.

**Domain docs**: [`platform-delivery`](domains/platform-delivery/overview.md)

### Identity-Access

**Owns**: edge authentication via Traefik and Authelia, forwarded identity trust boundaries, backend role enforcement, and anonymous public-session JWT bootstrap.

**Domain docs**: [`identity-access`](domains/identity-access/overview.md)

### Core-Regatta

**Owns**: the event-sourced domain core for regattas, athletes, crews, entries, regatta setup, event history, and projection foundations.

**Domain docs**: [`core-regatta`](domains/core-regatta/overview.md)

### Rules-Draw

**Owns**: rulesets, blocks, bib pools, draw generation, draw publication, and the scheduling constraints that feed public and operator workflows.

**Domain docs**: [`rules-draw`](domains/rules-draw/overview.md)

### Public-Delivery

**Owns**: versioned public APIs, cache policy, SSE delivery, public UI surfaces, formatting/i18n display behavior, and printable export presentation.

**Domain docs**: [`public-delivery`](domains/public-delivery/overview.md)

### Operator-Capture

**Owns**: operator tokens, capture sessions, line-scan manifests and tiles, marker workflows, offline synchronization, and station handoff flows.

**Domain docs**: [`operator-capture`](domains/operator-capture/overview.md)

### Adjudication

**Owns**: investigations, penalties, DSQ and exclusion decisions, approval gates, and result-state transitions that affect publication.

**Domain docs**: [`adjudication`](domains/adjudication/overview.md)

### Finance

**Owns**: payment status tracking, club and entry finance summaries, invoice generation, and financial bulk operations.

**Domain docs**: 

*[truncated — see source for full prompt]*