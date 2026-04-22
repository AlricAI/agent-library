# Plan

> ## Goal Description
Implement the complete 7-Layer enforcement stack for VEIL, transforming it from a "Foundation" MVP to a functional "Living Identit

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# VEIL 7-Layer Sentinel Implementation Plan

## Goal Description
Implement the complete 7-Layer enforcement stack for VEIL, transforming it from a "Foundation" MVP to a functional "Living Identity Firewall". 
**Architecture Alignment**: As per `Master_Architecture_v2.1.md`, VEIL (Reflexes) acts as a **Sidecar** living next to the Agent.
This plan establishes the "Reflex" layer (Java Sidecar) and the "Traffic Controller" logic.

## Technology Stack [CONFIRMED]
- **Core Backend**: `Java 17`, `Spring Boot 3.x`
- **Sidecar/Proxy**: `Envoy Proxy` (v1.28+), `Docker Compose`
- **Data & State**: `Redis` (Hot Cache/Nonces), `PostgreSQL` (Ledger/Cold Storage)
- **Intelligence**: `Google Gemini 1.5 Flash` (via Java SDK/REST)
- **Security**: `Java Security` (SHA-256), `Twilio/Auth0` (JWT - Optional), `OPA` (Policy - mocked initially)

## Required Agent Skills
The following agent skills will be enabled and utilized during development:
- **`java-pro`**: Primary for Backend Core. Implementing robust Spring Boot 3.x services, TrafficController logic, and advanced Java 17 features.
- **`backend-architect`**: Primary for Infrastructure. Designing the Envoy sidecar interplay, Docker orchestration, and system decoupling.
- **`backend-security-coder`**: Primary for Safety. Writing secure implementations for Policy Engine (Layer 3), Runtime Identity (Layer 1), and Ledger (Layer 7).
- **`ai-engineer`**: Primary for Intelligence. Implementing the CouncilService (Layer 4) and its integration with Gemini models.
- **`tdd-orchestrator` / `unit-testing-test-generate`**: Establishing the quality gate with JUnit 5 tests and Red-Green-Refactor workflows.

## Workflow & Process [CRITICAL]
> [!IMPORTANT]
> **Version Control Protocol**: Every change must be committed and pushed to GitHub immediately upon successful verification.
> A "change" is defined as a completed implementation step (e.g., "Implemented TrafficLightService").
> **Commit Message Standard**: `feat(veil): [Layer X] Description of co

*[truncated — see source for full prompt]*