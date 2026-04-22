# FASE 4 README

> ## 🎯 Overzicht

Deze fase uitbreidt VorstersNV met een **AI-gestuurde Smart Home** op een lokale Linux-server. Doel: Volledige automatisering met lok

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 📚 VorstersNV – Fase 4 Home Assistant & MCP AI

## 🎯 Overzicht

Deze fase uitbreidt VorstersNV met een **AI-gestuurde Smart Home** op een lokale Linux-server. Doel: Volledige automatisering met lokale controle, geen cloud-afhankelijkheid.

---

## 📦 Wat is in deze Fase

### 1️⃣ **Documentatie** (Compleet)

| Document | Beschrijving |
|----------|-------------|
| `FASE_4_HOMEASSISTANT_MCP.md` | Complete Fase 4 architectuur & installatie plan |
| `FASE_4_QUICKSTART.md` | Stap-voor-stap quick start guide |
| `HOW_TO_AGENTS.md` | Gedetailleerde agent development guide |

### 2️⃣ **MCP Server** (Klaar)

- ✅ FastAPI server (`mcp-server/main.py`)
- ✅ Home Assistant API integratie
- ✅ Ollama LLM integratie
- ✅ Health checks & monitoring
- ✅ Docker setup

### 3️⃣ **Agents** (Klaar)

- ✅ `home_automation_agent.yml` – Verlichting & climate control
- ✅ `energy_management_agent.yml` – Energieverbruik optimalisatie
- ✅ `security_agent.yml` – Veiligheidsbewaking

### 4️⃣ **Prompts** (Klaar)

- ✅ System prompts voor alle agents
- ✅ Pre-prompts met voorbeelden
- ✅ Evaluatie-richtlijnen

---

## 🚀 Installatiepad

### Week 1-2: Server Voorbereiding

```bash
# Op oude laptop (Linux server)
1. Ubuntu 22.04 LTS installeren
2. Docker + Docker Compose
3. Git clonen
4. SSH-access testen
```

### Week 2-3: Home Assistant

```bash
1. Home Assistant container starten
2. Devices toevoegen (Zigbee, WiFi, Cloud)
3. Scenes & Automations configureren
4. Token genereren
```

### Week 3-4: MCP Server

```bash
1. MCP Server container starten
2. Home Assistant API testen
3. Ollama integratie testen
4. Agents laden en testen
```

### Week 4-5: Agents

```bash
1. Home Automation Agent testen
2. Energy Management Agent testen
3. Security Agent testen
4. Feedback loop instellen
```

### Week 5-6: Integratie

```bash
1. VorstersNV ↔ MCP Server webhooks
2. Order-triggered automations
3. Payment confirmations via HA
4. Monitoring dashboard
```

---

## 📋 File Structuur

```
Personal_project_VorstersNV/


*[truncated — see source for full prompt]*