# CLAUDE

> This guide provides comprehensive instructions for creating **cs-* prefixed agents** that seamlessly integrate with the 42 production skills in this repository.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Agent Development Guide

This guide provides comprehensive instructions for creating **cs-* prefixed agents** that seamlessly integrate with the 42 production skills in this repository.

## Agent Architecture

### What are cs-* Agents?

**cs-* agents** are specialized Claude Code agents that orchestrate the 177 existing skills. Each agent:
- References skills via relative paths (`../../marketing-skill/`)
- Executes Python automation tools from skill packages
- Follows established workflows and templates
- Maintains skill portability and independence

**Key Principle**: Agents ORCHESTRATE skills, they don't replace them. Skills remain self-contained and portable.

### ClawHub Publishing Constraints

When skills are published to **ClawHub** (clawhub.com):
- **cs- prefix for slug conflicts only** — applies only on the ClawHub registry when another publisher already owns the slug. Repo folder names and local skill names are never renamed.
- **No paid/commercial service dependencies** — skills must not require paid third-party API keys or commercial services unless provided by the project itself.
- **plugin.json** — ONLY fields: `name`, `description`, `version`, `author`, `homepage`, `repository`, `license`, `skills: "./"`.
- **Rate limit:** 5 new skills/hour on ClawHub. Use drip publishing for bulk operations.

### Production Agents

**16 Agents Currently Available**:

| Agent | Domain | Description |
|-------|--------|-------------|
| [cs-content-creator](marketing/cs-content-creator.md) | Marketing | AI-powered content creation with brand voice consistency and SEO optimization |
| [cs-demand-gen-specialist](marketing/cs-demand-gen-specialist.md) | Marketing | Demand generation and customer acquisition specialist |
| [cs-ceo-advisor](c-level/cs-ceo-advisor.md) | C-Level | Strategic leadership advisor for CEOs |
| [cs-cto-advisor](c-level/cs-cto-advisor.md) | C-Level | Technical leadership advisor for CTOs |
| [cs-product-manager](product/cs-product-manager.md) | Prod

*[truncated — see source for full prompt]*