# AGENT PLAN SUMMARY

> ## 🎯 Doel van dit Plan

Dit plan beschrijft hoe je **VorstersNV** van begin tot eind opbouwt **met je 8 bestaande agents als centrale uitvoerders**.


## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 📚 AGENT-GEBASEERD PLAN SAMENVATTING – VorstersNV Fase 3-5

## 🎯 Doel van dit Plan

Dit plan beschrijft hoe je **VorstersNV** van begin tot eind opbouwt **met je 8 bestaande agents als centrale uitvoerders**.

In plaats van traditionele code schrijven, routeer je alles naar de juiste agent, laat de agent werken, en bouw je daar verder op.

---

## 📊 De 8 Agents – Jouw Workforce

```
┌─────────────────────────────────────────────────────────────┐
│              JE AGENT TEAM (8 AGENTS)                        │
├─────────────────────────────────────────────────────────────┤
│                                                               │
│  🤖 AGENT 1: Klantenservice Agent (llama3)                 │
│     └─ Wat: Klantenvragen, order info, retourverzoeken      │
│     └─ Waar: /api/support/chat endpoint                     │
│     └─ Sub-agents: Retour, Email, Fraude                    │
│                                                               │
│  🤖 AGENT 2: Order Verwerking Agent (llama3)               │
│     └─ Wat: Order validatie, bevestiging, facturen          │
│     └─ Waar: POST /webhooks/order-created webhook           │
│     └─ Sub-agents: Fraude, Email, Voorraad                  │
│                                                               │
│  🤖 AGENT 3: Product Beschrijving Agent (mistral)          │
│     └─ Wat: Productbeschrijvingen, USPs, FAQs              │
│     └─ Waar: POST /api/products/generate-description        │
│     └─ Sub-agents: Geen                                     │
│                                                               │
│  🤖 AGENT 4: SEO Agent (mistral)                           │
│     └─ Wat: SEO optimalisatie, keywords, meta tags          │
│     └─ Waar: POST /api/products/seo-optimize                │
│     └─ Sub-agents: Geen                                     │
│                                                               │
│  🤖 AGENT 5: Fraude Detectie Agent (llama3)                │
│    

*[truncated — see source for full prompt]*