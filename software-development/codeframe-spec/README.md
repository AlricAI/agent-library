# CODEFRAME SPEC

> **Fully Remote Autonomous Multiagent Environment for Coding**

---

## Executive Summary

CodeFRAME is an autonomous AI coding system that manages sof

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# CodeFRAME Technical Specification v1.0

**Fully Remote Autonomous Multiagent Environment for Coding**

---

## Executive Summary

CodeFRAME is an autonomous AI coding system that manages software development through coordinated agent swarms. Built initially on Claude Code with support for multiple LLM providers, it enables developers to launch projects, define requirements through Socratic dialogue, and let AI agents work autonomously while maintaining human oversight through asynchronous interruption patterns.

**Key Innovation**: Virtual Project context management - React-like diffing for agent memory that hot-swaps context based on importance scoring, preventing context pollution and enabling long-running autonomous execution.

---

## Table of Contents

1. [Architecture Overview](#architecture-overview)
2. [Core Components](#core-components)
3. [Virtual Project Context System](#virtual-project-context-system)
4. [Agent Management & Maturity](#agent-management--maturity)
5. [Task Coordination](#task-coordination)
6. [Notification System](#notification-system)
7. [State Persistence & Recovery](#state-persistence--recovery)
8. [Multi-Provider Support](#multi-provider-support)
9. [Test Automation](#test-automation)
10. [Status Server & UI](#status-server--ui)
11. [15-Step Workflow Integration](#15-step-workflow-integration)
12. [Database Schema](#database-schema)
13. [API Specifications](#api-specifications)
14. [MVP Scope & Roadmap](#mvp-scope--roadmap)

> NOTE: This is a **technical design** document. For up-to-date product requirements,
> user workflows, and E2E scenarios, see [PRD.md](../PRD.md). Sections below are
> annotated with implementation status as of 2025-11-21.

---

## Architecture Overview

### High-Level System Design

```
┌─────────────────────────────────────────────────────────────┐
│                    CodeFRAME CLI / API                       │
│  Commands: init, start, pause, resume, status, config        │
└───────────────────┬─────────────

*[truncated — see source for full prompt]*