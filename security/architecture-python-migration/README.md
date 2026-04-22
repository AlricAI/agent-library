# Architecture Python Migration

> **Date:** 2026-02-05
**Status:** APPROVED
**Context:** Migration to Python/FastAPI with "Full Proof" Security Hardening.

## 1. Executive Summary

Thi

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# VEIL: Python Architecture Migration Plan (v4.0 - Full Proof)

**Date:** 2026-02-05
**Status:** APPROVED
**Context:** Migration to Python/FastAPI with "Full Proof" Security Hardening.

## 1. Executive Summary

This architecture redesigns VEIL as a **Python-Native Security Mesh**. It implements a **Zero Trust** philosophy where every component is untrusted and verified. It combines the "Reflex" speed layer with the "Brain" cognitive layer, hardened against the **STRIDE** threat model.

**Core Philosophy:**
*   **The Hand (Mitmproxy):** A scriptable, transparency-preserving proxy that physically intercepts traffic.
*   **The Nervous System (FastAPI):** An async decision engine that processes requests, consults the Brain, and enforces policy.
*   **The Brain (Gemini 1.5):** The cognitive layer for judgment and synthesis.

## 2. Technology Stack (Python-First)

| Component | Role | Technology | Version | Justification |
| :--- | :--- | :--- | :--- | :--- |
| **Edge Proxy** | **The Smart Valve** (Layer 0) | **Mitmproxy** | 10.x | Native Python scripting for interception. Replaces Envoy sidecar complexity with pure Python logic. |
| **Reflex Engine** | **The Speed Layer** (Layers 1-5) | **FastAPI** | 0.109+ | High-performance (ASGI), native Pydantic validation, and excellent async support for non-blocking I/O. |
| **Task Queue** | **Async Offloading** (Layer 7+) | **ARQ + Redis** | 0.25+ | Simpler and faster than Celery for async job processing (e.g., Ledger sealing, Brain synthesis) in FastAPI. |
| **Policy Engine** | **Deterministic Rules** (Layer 3) | **OPA (Open Policy Agent)** | Latest | Industry standard. Decouples "Business Rules" (Rego) from application logic. |
| **Intelligence** | **The Brain** (Layer 4) | **Google GenAI SDK** | 0.4.x | Native, First-Class access to Gemini 1.5 Flash (Reflex) and Pro (Brain). |
| **Memory** | **Vector Store** | **Pgvector (PostgreSQL)** | 15+ | Stores embeddings of audit logs for semantic search and "Recalling" past threats. |
|

*[truncated — see source for full prompt]*