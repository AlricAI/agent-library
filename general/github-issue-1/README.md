# Github Issue

> ## Overview

This epic tracks the implementation of **Hypergoat**, a Go port of [Quickslice](https://github.com/quickslice/quickslice) - an AT Protoco

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# [Epic] Port Quickslice to Go - Hypergoat Implementation

## Overview

This epic tracks the implementation of **Hypergoat**, a Go port of [Quickslice](https://github.com/quickslice/quickslice) - an AT Protocol AppView server that indexes Lexicon-defined records and exposes them via a dynamically-generated GraphQL API.

**Goal:** Feature parity with Quickslice while leveraging Go's performance characteristics and ecosystem.

**Estimated Timeline:** 8-10 weeks

---

## Background

Quickslice is written in Gleam (targeting Erlang/OTP) and provides:
- Dynamic GraphQL schema generation from AT Protocol Lexicons
- Real-time sync via Jetstream WebSocket
- OAuth 2.0 server with DPoP and AT Protocol bridge
- Multi-database support (SQLite/PostgreSQL)
- GraphQL subscriptions via WebSocket
- Batch backfill from AT Protocol relays

Hypergoat will maintain API compatibility so existing quickslice-client-js clients work unchanged.

---

## Technology Decisions

| Component | Library | Rationale |
|-----------|---------|-----------|
| HTTP | chi | Lightweight, idiomatic, good middleware |
| Database | pgx + modernc/sqlite | Native drivers, no CGO for SQLite |
| GraphQL | graphql-go/graphql | Runtime schema generation |
| WebSocket | nhooyr/websocket | Modern, context-aware |
| JWT/JOSE | golang-jwt + go-jose | Industry standard |
| Config | caarlos0/env | Struct tags, validation |

---

## Implementation Phases

### Phase 1: Foundation (Week 1-2)
- [ ] Project setup (go.mod, Makefile, CI)
- [ ] Configuration management
- [ ] Database executor abstraction (SQLite + PostgreSQL)
- [ ] Core repositories (records, actors, lexicons, config)
- [ ] Database migrations

### Phase 2: Lexicon & GraphQL Core (Week 2-3)
- [ ] Lexicon JSON parser
- [ ] Lexicon registry for cross-references
- [ ] NSID utilities
- [ ] GraphQL type mapping
- [ ] WHERE input types
- [ ] Connection types (Relay spec)
- [ ] Multi-pass schema builder

### Phase 3: GraphQL API (Week 3-4)
- [ ] Record fetcher interface

*[truncated — see source for full prompt]*