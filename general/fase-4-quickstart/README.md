# FASE 4 QUICKSTART

> ## ✅ Status Check

Je hebt nu:
- ✅ VorstersNV webshop & API draaiend (Docker)
- ✅ Basis project-infra en agents
- 🔄 Linux server voorbereiding nodig


## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 🚀 Fase 4 – Quick Start Guide

## ✅ Status Check

Je hebt nu:
- ✅ VorstersNV webshop & API draaiend (Docker)
- ✅ Basis project-infra en agents
- 🔄 Linux server voorbereiding nodig
- 📦 MCP Server skeleton klaar

---

## 📋 Volgende Stappen (Deze Week)

### Stap 1: Linux Server Voorbereiding

Ga naar je oude laptop en run:

```bash
# SSH in als sudo user
ssh user@laptop_ip

# Update systeem
sudo apt update && sudo apt upgrade -y

# Install Docker
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh

# Add user to docker group
sudo usermod -aG docker $USER
newgrp docker

# Verify installation
docker --version
docker compose --version
```

### Stap 2: Clone VorstersNV Project

```bash
# Clone het project
git clone https://github.com/koenvorster/Personal_project_VorstersNV.git
cd Personal_project_VorstersNV

# Copy environment file
cp .env.example .env

# Edit .env met server-speficieke waarden
nano .env
```

### Stap 3: Start Home Assistant

```bash
# Maak config directory
mkdir -p config

# Start Home Assistant
docker compose -f docker-compose.yml up -d homeassistant

# Check logs
docker logs homeassistant -f

# Access op http://laptop_ip:8123
```

### Stap 4: Configure Home Assistant

1. Open http://laptop_ip:8123
2. Klik "Create My Smart Home"
3. Zet je locatie (Amsterdam, NL)
4. Voeg integraties toe:
   - MQTT (optioneel, voor Zigbee)
   - REST (optioneel, voor externe systemen)
5. Voeg devices toe via Integrations

### Stap 5: Genereer Home Assistant Token

```bash
# In Home Assistant UI:
# Profile → Security → Create Token
# Kopieer en sla op in .env:
HA_TOKEN=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
```

### Stap 6: Start MCP Server

```bash
# In project directory
docker compose -f docker-compose.yml up -d mcp-server

# Check status
curl http://localhost:8000/health

# Check logs
docker logs mcp-server -f
```

### Stap 7: Test Integration

```bash
# Test Home Assistant connection
curl -H "Authorization: Bearer $HA_TOKEN" \
     http://local

*[truncated — see source for full prompt]*