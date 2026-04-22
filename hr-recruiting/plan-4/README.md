# PLAN

> ## Overzicht

Dit document beschrijft het complete plan voor de VorstersNV applicatie: een zakelijk platform met webshop, aangedreven door lokale AI-a

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# VorstersNV – Projectplan

## Overzicht

Dit document beschrijft het complete plan voor de VorstersNV applicatie: een zakelijk platform met webshop, aangedreven door lokale AI-agents (via Ollama) en geautomatiseerde webhooks en pipelines.

---

## Plan Modes

Het project werkt met drie **plan-modes** die bepalen in welke fase je werkt:

| Mode | Beschrijving |
|------|-------------|
| `plan` | Ontwerpen van nieuwe features, agent-configuraties en prompt-strategieën |
| `build` | Actieve ontwikkeling, integraties en pipeline-configuratie |
| `review` | Testen, evalueren van agent-output, prompt-iteraties en optimalisatie |

De huidige actieve mode wordt bijgehouden in [`mode.yml`](./mode.yml).

---

## Projectfasen

### Fase 1 – Fundament ✅
- [x] Projectstructuur aanmaken
- [x] Plan-document opstellen
- [x] Agent-definities (YAML) aanmaken
- [x] Prompt-boeken en pre-prompts structureren
- [x] Webhook-handlers (FastAPI) inrichten
- [x] GitHub Actions pipelines configureren
- [x] Ollama lokale AI-integratie opzetten
- [x] Docker Compose voor lokale ontwikkeling

### Fase 2 – Agents & Prompts ✅
- [x] Klantenservice-agent verbeteren met feedback-loop (v1.1 + sub-agents)
- [x] Product-beschrijving agent iteratief optimaliseren (v1.1 + USP + FAQ)
- [x] SEO-agent fine-tunen op webshop-producten (v1.1 + interne linking)
- [x] Order-verwerking agent bouwen (v1.1 + fraude pre-check + batch)
- [x] Sub-agents aanmaken: fraude_detectie, retour_verwerking, email_template, voorraad_advies
- [x] Multi-agent orkestratie implementeren (ParallelStep + 3 workflows)
- [x] Tuple-bug gerepareerd in agent_runner + orchestrator

### Fase 3 – Webshop & Business Logica 🔄 (in uitvoering)
- [x] Orders router volledig verbonden met PostgreSQL (create, list, get, update_status, statistieken)
- [x] Inventory router volledig verbonden met PostgreSQL (overzicht, set, aanpassen, low-stock alerts)
- [x] Notifications router aangemaakt (email_template_agent integratie via AgentLog)
- [x] Dashboard rou

*[truncated — see source for full prompt]*