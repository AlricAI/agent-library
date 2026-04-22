# CREW README

> **Persistent crew with brain integration, game server bridges, and captain communications.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# N'og nog: Crew Expansion System v1.0

**Persistent crew with brain integration, game server bridges, and captain communications.**

---

## 🎯 Overview

Your N'og nog crew now lives beyond the browser. This system provides:

- **5-10 Persistent Crew Members** with skills, levels, and equipment
- **AOS Brain Integration** for autonomous AI-driven decisions
- **Real Game Server Connections** (Roblox, Minecraft)
- **Captain Communications** via email and Telegram
- **Expedition Logging** with photos from crew

---

## 📁 Architecture

```
nognog/crew/
├── core/
│   ├── CrewManager.js        # Persistence + crew lifecycle
│   ├── CrewCoordinator.js    # Main orchestrator
│   └── BrainCrew.js          # AOS brain integration
├── integrations/
│   └── GameBridge.js         # Roblox + Minecraft bridges
├── comms/
│   └── CrewComms.js          # Email + Telegram
├── storage/crew/             # Crew JSON files
└── main.js                   # Full system entry

nognog/crew-lite.js           # Lightweight running system (ACTIVE)
nognog/crew-bridge.js         # Socket bridge to brain
```

---

## ⚡ Quick Commands

### Status
```bash
cd /root/.openclaw/workspace/nognog
node crew-lite.js list
```

### Manual Report
```bash
node crew-lite.js status
```

### Rest Crew
```bash
node crew-lite.js rest 8
```

### Socket Bridge
```bash
# Crew socket
echo '{"cmd":"status"}' | nc -U /tmp/nognog_crew.sock

# Direct brain query
echo '{"cmd":"brain","params":{"decide":true}}' | nc -U /tmp/nognog_crew.sock
```

---

## 🎖️ Current Crew (Generated)

| Name | Role | Level | Status |
|------|------|-------|--------|
| **Vex** | PILOT | Rookie | ACTIVE |
| **Nyx** | ENGINEER | Rookie | ACTIVE |
| **Jax** | SCIENTIST | Rookie | ACTIVE |
| **Luna** | COMBAT | Rookie | ACTIVE |
| **Aria** | MEDIC | Rookie | ACTIVE |

---

## 🧠 Brain Integration

The crew system connects to your AOS brain at `/tmp/aos_brain.sock`:

- **Decision Making**: Brain processes crew personalities + context
- **Autonomous 

*[truncated — see source for full prompt]*