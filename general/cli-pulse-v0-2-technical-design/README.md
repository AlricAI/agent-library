# CLI Pulse V0.2 Technical Design

> ## 1. Design Goal

v0.2 should establish a stable foundation for multi-provider observability without forcing a full architecture rewrite later.

This

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# CLI Pulse v0.2 Technical Design

## 1. Design Goal

v0.2 should establish a stable foundation for multi-provider observability without forcing a full architecture rewrite later.

This design focuses on:

- provider extensibility
- project-level aggregation
- estimated cost computation
- stronger alert routing
- helper data quality improvements

## 2. System Boundaries

### iOS App

- renders dashboard, projects, sessions, devices, alerts, settings
- consumes backend APIs only
- does not hold provider secrets
- handles deep links from push notifications

### Backend API

- remains the source of truth
- owns provider normalization, aggregation, cost rollups, alert evaluation
- persists user, device, session, provider, project, and alert state

### Device Helper

- collects local execution signals
- performs provider inference and lightweight metadata extraction
- sends normalized sync payloads
- never exposes raw secrets to the phone

## 3. Architecture Changes

## 3.1 Provider Adapter Layer

Introduce an adapter contract in backend and helper.

Recommended interface:

- `provider_key`
- `display_name`
- `capabilities`
- `collect_usage()`
- `collect_quota()`
- `collect_cost_inputs()`
- `collect_health()`

Initial providers:

- Codex
- Gemini
- Claude
- OpenRouter
- Ollama

Key rule:

The app must render provider data through shared view models and shared DTOs. No provider-specific page type should be required.

## 3.2 Domain Model

### ProviderRecord

- id
- provider_key
- display_name
- status
- quota
- remaining
- usage_today
- usage_week
- estimated_cost_today
- estimated_cost_week
- capability_flags

### ProjectRecord

- id
- name
- normalized_key
- usage_today
- usage_week
- estimated_cost_today
- estimated_cost_week
- active_session_count
- device_count
- top_provider
- unresolved_alert_count

### SessionRecord

Extend current session model with:

- project_id or normalized project key
- cost_estimate
- collection_method
- collection_confidence

### AlertRecor

*[truncated — see source for full prompt]*