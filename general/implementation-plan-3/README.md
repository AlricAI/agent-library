# IMPLEMENTATION PLAN

> > Comprehensive porting plan from Quickslice (Gleam) to Hypergoat (Go)

## Overview

This document tracks the implementation of Hypergoat, a Go port o

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Hypergoat Implementation Plan

> Comprehensive porting plan from Quickslice (Gleam) to Hypergoat (Go)

## Overview

This document tracks the implementation of Hypergoat, a Go port of [Quickslice](https://github.com/quickslice/quickslice). Quickslice is an AT Protocol AppView server written in Gleam that indexes Lexicon-defined records and exposes them via a dynamically-generated GraphQL API.

**Target:** Feature parity with Quickslice while leveraging Go's performance and ecosystem.

**Estimated Timeline:** 8-10 weeks

---

## Architecture Decisions

### Technology Choices

| Component | Quickslice (Gleam) | Hypergoat (Go) | Rationale |
|-----------|-------------------|----------------|-----------|
| HTTP | wisp/mist | chi | Lightweight, idiomatic, good middleware |
| Database | sqlight/pog | pgx + modernc/sqlite | Native drivers, no CGO for SQLite |
| GraphQL | swell | graphql-go/graphql | Runtime schema generation (like Quickslice) |
| WebSocket | mist | nhooyr/websocket | Modern, context-aware |
| JSON | gleam_json | encoding/json + gjson | Standard library + fast queries |
| JWT/JOSE | jose | golang-jwt + go-jose | Industry standard libraries |
| Logging | logging | slog | Standard library (Go 1.21+) |
| Config | envoy/dotenv | caarlos0/env | Struct tags, validation |

### Concurrency Model Translation

| Gleam/Erlang Pattern | Go Equivalent |
|---------------------|---------------|
| Actor with `process.Subject` | Goroutine with `chan T` |
| `group_registry` (PubSub) | `sync.Map` + channels / custom broker |
| ETS tables | `sync.Map` or `groupcache` |
| Supervisor trees | `errgroup` or custom manager |
| `process.sleep_forever()` | `select {}` or signal handling |

---

## Phase 1: Foundation (Week 1-2) ✅ COMPLETE

### 1.1 Project Setup

- [x] Initialize Go module
- [x] Create project directory structure
- [x] Configure `.golangci.yml` for linting
- [x] Set up Makefile with common tasks
- [x] Create Dockerfile and docker-compose.yml
- [x] Set up GitHub Action

*[truncated — see source for full prompt]*