# FASE 4 HOMEASSISTANT MCP

> ## 📋 Overzicht

Deze fase breidt het VorstersNV-project uit met **Home Assistant** op een Linux-server met **MCP (Model Context Protocol) AI-integrat

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Fase 4 – Home Assistant + MCP AI Integration

## 📋 Overzicht

Deze fase breidt het VorstersNV-project uit met **Home Assistant** op een Linux-server met **MCP (Model Context Protocol) AI-integratie**. Dit biedt:

- **Lokale controle** van smart home-apparaten
- **AI-gestuurde automatisering** via MCP agents
- **Offline-first** architectuur (geen cloud-afhankelijkheid)
- **Integratie** met bestaande VorstersNV agents

---

## 🎯 Doelstelling

```
┌─────────────────────────────────────────────────────────┐
│           VorstersNV + Home Assistant Infra             │
├──────────────────┬──────────────────┬──────────────────┤
│  Webshop & API   │  MCP AI Layer    │ Smart Home (HA)  │
│  (Huidige setup) │  (Agents)        │  (Linux Server)  │
├──────────────────┼──────────────────┼──────────────────┤
│ - Orders/Inv     │ - Home control   │ - Lights         │
│ - Dashboard      │ - Energy mgmt    │ - Climate        │
│ - Payments       │ - Automations    │ - Security       │
│ - Notifications  │ - Learning       │ - Devices        │
└──────────────────┴──────────────────┴──────────────────┘
         │                  │                  │
         └──────────────────┴──────────────────┘
              Communicatie via REST/Webhooks
```

---

## 📦 Installatie-plan

### Stap 1: Linux Server voorbereiding (op oude laptop)

**Wat nodig:**
- [ ] Ubuntu 22.04 LTS (of recent Debian-variant)
- [ ] SSH-access configureren
- [ ] Docker + Docker Compose

**Commando's:**
```bash
# Update systeem
sudo apt update && sudo apt upgrade -y

# Docker installeren
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh

# Huidige user toevoegen aan docker groep
sudo usermod -aG docker $USER
newgrp docker

# Docker Compose installeren
sudo curl -L "https://github.com/docker/compose/releases/download/v2.20.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```

### Stap 2: Home Assistant Setup

**docker-compo

*[truncated — see source for full prompt]*