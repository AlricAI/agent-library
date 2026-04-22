# README

> Dit zijn de **25 runtime agents** die het VorstersNV platform lokaal aandrijven via [Ollama](https://ollama.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# VorstersNV — Ollama Agent Catalogue

Dit zijn de **25 runtime agents** die het VorstersNV platform lokaal aandrijven via [Ollama](https://ollama.com).
Ze worden aangeroepen door `api/routers/agents.py` via de `PromptIterator` klasse.

> **Let op:** Dit zijn **productagents** die het webshop-platform bedienen.
> Ze zijn _niet_ dezelfde als de GitHub Copilot dev-agents in `.github/agents/` of de Claude Code agents in `.claude/agents/`.
> Zie [Agent Taxonomy](#agent-taxonomy) voor het onderscheid.

---

## Agent Taxonomy

Het project heeft **drie lagen** van AI agents:

| Laag | Locatie | Doel | Runtime |
|------|---------|------|---------|
| **Runtime agents** (dit bestand) | `agents/*.yml` | Bedienen het webshop-platform voor klanten | Ollama (llama3 / mistral) |
| **Copilot dev agents** | `.github/agents/` | Ondersteunen Koen bij development in VS Code / GitHub | GitHub Copilot |
| **Claude dev agents** | `.claude/agents/` | Ondersteunen Koen bij complexe taken in Claude Code | Claude (Anthropic) |

---

## Agent Overzicht

### Orchestrators & Architectuur

| Agent | Model | Temp | Rol |
|-------|-------|------|-----|
| `architect_agent` | llama3 | 0.35 | Top-level Solution Architect — ontwerpt DDD-architectuur, delegeert naar developer_agent + test_orchestrator |
| `test_orchestrator_agent` | llama3 | 0.3 | Coördineert alle test sub-agents, definieert teststrategieën |

### Webshop & Klantinteractie

| Agent | Model | Temp | Rol |
|-------|-------|------|-----|
| `checkout_begeleiding_agent` | llama3 | 0.3 | Begeleidt klant door checkout-flow, FAQ, winkelwagenhulp |
| `klantenservice_agent` | llama3 | 0.4 | Algemene klantenservice, klachten, retouren, FAQ |
| `aanbeveling_agent` | mistral | 0.6 | Productaanbevelingen op basis van browsgeschiedenis & profiel |
| `loyaliteit_agent` | llama3 | 0.5 | Beheert loyalty punten, rewards, VIP-acties |
| `betaling_status_agent` | llama3 | 0.2 | Status-updates Mollie-betalingen, webhook verwerking |
| `order_verwerking_agent

*[truncated — see source for full prompt]*