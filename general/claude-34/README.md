# CLAUDE

> MiroFish predicts and simulates real-world scenarios using multi-agent technology.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# MiroFish — AI Swarm Intelligence Engine

MiroFish predicts and simulates real-world scenarios using multi-agent technology. It builds knowledge graphs from seed data (news, policies, stories), spawns thousands of autonomous AI agents with independent personas and memory, then simulates social dynamics (Twitter/Reddit) to generate predictive reports.

## Quick Start

### Prerequisites
- Node.js >= 18
- Python 3.11–3.12
- `uv` package manager

### Setup

```bash
# 1. Configure environment
cp .env.example .env
# Fill in: LLM_API_KEY, LLM_BASE_URL, LLM_MODEL_NAME, ZEP_API_KEY

# 2. Install everything
npm run setup:all

# Or step-by-step:
npm run setup          # Node deps + frontend
npm run setup:backend  # Python venv via uv
```

### Run

```bash
npm run dev          # Starts frontend (:3000) + backend (:5001) concurrently

# Or separately:
npm run frontend     # Vue frontend on http://localhost:3000
npm run backend      # Flask backend on http://localhost:5001
```

### Docker Alternative

```bash
cp .env.example .env
docker compose up -d   # Ports 3000 + 5001
```

## Environment Variables (.env)

| Variable | Required | Description |
|----------|----------|-------------|
| `LLM_API_KEY` | Yes | API key for any OpenAI SDK-compatible LLM |
| `LLM_BASE_URL` | Yes | LLM endpoint URL |
| `LLM_MODEL_NAME` | Yes | Model name (e.g. `qwen-plus`) |
| `ZEP_API_KEY` | Yes | Zep Cloud API key (free tier works) |
| `LLM_BOOST_API_KEY` | No | Secondary faster LLM for acceleration |
| `LLM_BOOST_BASE_URL` | No | Boost LLM endpoint |
| `LLM_BOOST_MODEL_NAME` | No | Boost model name |

## Project Structure

```
mirofish/
├── frontend/          # Vue 3 + Vite + D3.js
│   └── src/
│       ├── views/     # Page components (Home, MainView, SimulationView, etc.)
│       ├── components/# Step1-5 workflow components, GraphPanel
│       └── api/       # API client modules
├── backend/           # Python Flask
│   ├── run.py         # Entry point (:5001)
│   ├── app/
│   │   ├── api/       # 

*[truncated — see source for full prompt]*