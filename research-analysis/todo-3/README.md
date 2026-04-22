# Todo

> - [x] Database schema: conversations, messages, ai_providers, usage_logs tables
- [x] AI Provider integration: Claude API
- [x] AI Provider integratio

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ClawX - Unified AI Command Center TODO

- [x] Database schema: conversations, messages, ai_providers, usage_logs tables
- [x] AI Provider integration: Claude API
- [x] AI Provider integration: Gemini API
- [x] AI Provider integration: Perplexity API
- [x] AI Provider integration: Grok API
- [x] AI Provider integration: Ollama (local)
- [x] AI Provider integration: Manus built-in LLM
- [x] tRPC routers: chat, providers, analytics
- [x] Single prompt broadcast to multiple AIs simultaneously
- [ ] Response streaming from each AI model
- [x] Dashboard layout with sidebar navigation
- [x] Chat interface with model selector (individual + broadcast mode)
- [x] Multi-panel response display for broadcast mode
- [x] Conversation history with timestamps and token tracking
- [x] API credential management via environment variables
- [x] Usage analytics dashboard: token usage, response times, costs per model
- [ ] Ollama priority mode for heavy tasks to preserve API tokens
- [x] Dark theme with clean functional design

## JoshuaCLAW Governance System
- [x] Database schema: governance_proposals and governance_votes tables
- [x] Backend: JoshuaCLAW voting logic (7 voters, 4/7 majority, odd tiebreaker)
- [x] Backend: Two-tier system (Tier 1 Critical / Tier 2 Operational)
- [x] Frontend: Red/Green light vote panel with visual vote board
- [x] Frontend: Governance page with proposal creation and vote tracking
- [x] Sidebar navigation: Add Governance page link
- [x] Tests: JoshuaCLAW voting logic tests (22 tests passing)

## YouAndINotAI Backend Critical Fixes (Pre-Launch)
- [x] Fix #3: /verify/confirm must check actual payment before marking verified
- [x] Fix #5: JWT secret must fail-fast on startup, no fallback default
- [x] Fix #1: Remove Stripe from verify.py, webhooks.py, models.py, config.py — wire Square
- [x] Fix #2: Build Square webhook handler for Bot-Shield $1 and subscriptions
- [x] Fix #4: Create tests/ directory with auth, verification, and webhook tests
- [x] Push all

*[truncated — see source for full prompt]*