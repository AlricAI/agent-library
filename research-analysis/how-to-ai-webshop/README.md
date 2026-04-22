# HOW TO AI WEBSHOP

> > **Voor wie?** Ontwikkelaars, technische ondernemers en iedereen die nieuwsgierig is naar hoe je een echte webshop bouwt met lokale AI — zonder cloud-kosten of data die je bedrijf verlaat.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# How-To: Van nul naar AI-aangedreven webshop — het VorstersNV verhaal

> **Voor wie?** Ontwikkelaars, technische ondernemers en iedereen die nieuwsgierig is naar hoe je een echte webshop bouwt met lokale AI — zonder cloud-kosten of data die je bedrijf verlaat.

---

## Het begin: waarom dit project?

Alles begon met een simpele vraag: _"Kan ik een webshop bouwen die slim genoeg is om klanten te helpen, zonder dure abonnementen op ChatGPT of externe AI-diensten?"_

Het antwoord bleek: **ja, met Ollama, FastAPI en wat geduld**.

Dit is de stap-voor-stap handleiding van hoe ik VorstersNV heb opgebouwd — een volledig functioneel e-commerce platform met lokale AI-agents, een moderne webshop frontend, betalingen en een CI/CD pipeline.

---

## Wat heb je nodig?

### Hardware & OS
- Een PC of laptop met minstens **8 GB RAM** (16 GB aanbevolen voor Ollama)
- Windows 10/11, macOS of Linux (wij gebruikten Windows)
- Docker Desktop geïnstalleerd

### Software
- **Python 3.12** — de backend taal
- **Node.js 20+** — voor de Next.js frontend
- **Docker Compose** — voor PostgreSQL, Redis en Ollama lokaal
- **Git + GitHub** — versiebeheer en CI/CD
- **GitHub Copilot CLI** (optioneel maar *sterk* aanbevolen — dit is hoe we 90% van de code schreven)

### Kennis (basis volstaat)
- Basiskennis Python en JavaScript/TypeScript
- Begrip van REST APIs
- Docker-basis (images, containers, volumes)

---

## Stap 1: De AI lokaal draaien met Ollama

Ollama is een tool waarmee je grote taalmodellen (LLMs) lokaal op je eigen machine kunt draaien. Geen API-sleutels, geen kosten per request, geen data die je bedrijf verlaat.

```bash
# Installeer Ollama (zie ollama.ai)
# Start daarna modellen:
ollama pull llama3      # voor klantenservice en orderverwerking
ollama pull mistral     # voor SEO en productbeschrijvingen
```

### docker-compose.yml voor Ollama

```yaml
services:
  ollama:
    image: ollama/ollama
    ports:
      - "11434:11434"
    volumes:
      - ollama_data:/root/.ollama

  databas

*[truncated — see source for full prompt]*