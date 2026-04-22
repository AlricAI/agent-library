# VISION

> **Document Type:** Engineering Vision Document  
**Status:** Draft for Review  
**Author:** Moltler Team  
**Last Updated:** February 2026  

---

## 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Moltler: Vision & Technical Strategy

**Document Type:** Engineering Vision Document  
**Status:** Draft for Review  
**Author:** Moltler Team  
**Last Updated:** February 2026  

---

## Executive Summary

Moltler is a **skills framework for Elasticsearch** that enables users to build, share, and run reusable operations on their data. It addresses a fundamental gap in how organizations operationalize their Elasticsearch investments: the disconnect between platform capabilities and operational knowledge.

This document outlines the vision, problem space, technical approach, and strategic rationale for Moltler.

---

## Table of Contents

1. [The Problem](#the-problem)
2. [Vision](#vision)
3. [Why Now](#why-now)
4. [Technical Approach](#technical-approach)
5. [Why This Approach vs Alternatives](#why-this-approach-vs-alternatives)
6. [What Moltler Involves](#what-moltler-involves)
7. [Architecture](#architecture)
8. [Use Cases](#use-cases)
9. [Success Metrics](#success-metrics)
10. [Roadmap](#roadmap)
11. [Open Questions](#open-questions)

---

## The Problem

### Operational Knowledge is Trapped

Organizations invest heavily in Elasticsearch for observability, security, and search. They build sophisticated data pipelines, create detection rules, and develop operational procedures. But this knowledge is:

1. **Fragmented** - Spread across runbooks, wikis, Slack threads, and individual experts' heads
2. **Not reusable** - The same query patterns are reinvented across teams
3. **Not shareable** - Hard to package and distribute operational knowledge
4. **Not testable** - No way to validate that procedures still work
5. **Not versioned** - Changes aren't tracked, rollbacks are impossible

### The Expert Dependency Problem

When an incident occurs at 3 AM:
- Junior engineers struggle to know *what* to query
- Senior engineers get paged because they know *how* to investigate
- AI assistants can't help because they don't understand your data

The expertise required to effe

*[truncated — see source for full prompt]*