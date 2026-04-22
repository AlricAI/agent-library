# MEMORY ENABLED AGENTS ARCHITECTURE

> **Document Version:** 1.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Memory-Enabled Goal-Seeking Agents: Complete System Architecture

**Document Version:** 1.0
**Date:** 2026-02-14
**Status:** Ready for Implementation
**Architect:** Claude Sonnet 4.5

---

## Executive Summary

This specification defines the complete architecture for **memory-enabled goal-seeking agents** - autonomous learning agents that accumulate knowledge across sessions using a shared graph-based memory system. The system extracts amplihack's Kuzu memory infrastructure into a standalone library, enhances the goal agent generator to inject memory capabilities, and provides four specialized learning agents as reference implementations.

**Key Innovation:** Agents learn from experience. Each execution stores episodic and semantic memories, enabling future sessions to build on past successes and avoid repeated failures.

**Design Philosophy:** Ruthlessly simple, modular (brick design), zero-BS implementation. Every component has ONE clear responsibility with regeneratable specifications.

---

## Table of Contents

1. [System Overview](#1-system-overview)
2. [Module Specifications](#2-module-specifications)
3. [Data Flow Architecture](#3-data-flow-architecture)
4. [Security Model](#4-security-model)
5. [Four Learning Agents](#5-four-learning-agents)
6. [Testing Strategy](#6-testing-strategy)
7. [Implementation Plan](#7-implementation-plan)
8. [Risk Assessment](#8-risk-assessment)
9. [API Contracts](#9-api-contracts)
10. [Success Metrics](#10-success-metrics)

---

## 1. System Overview

### 1.1 High-Level Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                         USER INTERFACE                           │
│  amplihack new --memory-enabled --agent-type <type> goal.md     │
└───────────────────────────┬─────────────────────────────────────┘
                            │
                            ▼
┌─────────────────────────────────────────────────────────────────┐
│               GOAL AGENT GENERATOR (Enhanced)

*[truncated — see source for full prompt]*