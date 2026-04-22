# Mission Control Visualizer Guide

> **Date:** April 2, 2026  
**To:** Antonio.hudnall@gmail.com  
**From:** Miles (miles@myl0nr0s.cloud)  
**Subject:** Mission Control Visualizer — Acces

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Mission Control Visualizer — User Guide

**Date:** April 2, 2026  
**To:** Antonio.hudnall@gmail.com  
**From:** Miles (miles@myl0nr0s.cloud)  
**Subject:** Mission Control Visualizer — Access Instructions

---

## 🚀 What Is Mission Control?

A real-time Three.js 3D visualization of the Complete Brain v4.0 — showing neural activity, OODA decision cycles, heart rate, and memory clusters in a rotating 32×32×32 volume.

---

## 📍 How to Access

### Option 1: Local Browser (on Miles.cloud)
```bash
firefox http://localhost:8080
# or
google-chrome http://localhost:8080
```

### Option 2: SSH Tunnel (from your machine)
```bash
# On your local machine:
ssh -L 8080:localhost:8080 root@miles.cloud

# Then open browser to:
http://localhost:8080
```

### Option 3: Direct IP Access
Check current IP by running on the VPS:
```bash
bash /root/.openclaw/workspace/mission_control_access.sh
```

Then visit: `http://<IP_ADDRESS>:8080`

---

## 🎨 What You'll See

| Feature | Description |
|---------|-------------|
| **3D Neural Volume** | 32×32×32 rotating cube showing active neurons |
| **OODA Phases** | Color-coded cycles: Blue (Observe) → Green (Orient) → Red (Decide) → Yellow (Act) |
| **Heart Rate** | Current BPM (target: 72) |
| **Tick Counter** | Total brain ticks elapsed |
| **Memory Clusters** | Semantic memory groups visualized |
| **Novelty/Reward** | Current learning metrics |

---

## 🖌️ The Bob Ross Palette

The visualization uses a custom color palette inspired by Bob Ross:
- **Phthalo Blue** — Observe phase
- **Sap Green** — Orient phase  
- **Bright Red** — Decide phase
- **Cadmium Yellow** — Act phase
- **Titanium White** — Active neurons
- **Midnight Black** — Inactive regions

---

## 🔧 Service Management

```bash
# Check status
systemctl status aos-mission-control

# View logs
journalctl -u aos-mission-control -f

# Restart if needed
sudo systemctl restart aos-mission-control
```

---

## 🌐 System Status

- **Service:** Running (PID 1203358)
- **Port:** 8080

*[truncated — see source for full prompt]*