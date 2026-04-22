# Llm Report Models

> The platform can generate reports using **only open-source or free-tier LLMs**.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Report Generation: Open-Source LLMs (Llama, Falcon & FinGPT)

The platform can generate reports using **only open-source or free-tier LLMs**. **No paid API keys are required** (no OpenAI, Anthropic, or other commercial APIs).

## LLM options: all free / open source

| Option | Model | API key / cost | Env |
|--------|--------|----------------|-----|
| **1. Llama (Ollama)** | Llama 3.2, Mistral, etc. | **None** – local via [Ollama](https://ollama.com) | `LLAMA_URL=http://localhost:11434`, `LLAMA_MODEL=llama3.2` |
| **2. Falcon (Docker)** | TII Falcon 7B Instruct | **None** – self-hosted, open source | `FALCON_TGI_URL=http://localhost:8080` |
| **3. FinGPT local (Docker)** | distilgpt2 (default) or FinGPT | **None** for public models; optional free **HF_TOKEN** for gated models | `FINGPT_LOCAL_URL=http://localhost:8081` |
| **4. FinGPT (HuggingFace Inference API)** | FinGPT or other HF models | **Free** – use a free [HuggingFace token](https://huggingface.co/settings/tokens); free tier has rate limits | `HF_TOKEN=hf_xxx` |

If none are set, the API falls back to a **simulated** response so the app still works.

## Options (pick one or combine)

| Option | Model | How | Env |
|--------|--------|-----|-----|
| **1. Llama (Ollama)** | Llama 3.2, Mistral, etc. | Local Ollama server | `LLAMA_URL`, `LLAMA_MODEL` |
| **2. Falcon (Docker)** | TII Falcon 7B Instruct | Text Generation Inference (TGI) | `FALCON_TGI_URL=http://localhost:8080` |
| **3. FinGPT local (Docker)** | FinGPT or small HF model | Optional inference container | `FINGPT_LOCAL_URL=http://localhost:8081` |
| **4. FinGPT (HuggingFace API)** | FinGPT on HF Inference | No Docker; free HF token only | `HF_TOKEN=hf_xxx` |

---

## 1. Llama via Ollama (recommended for report generation)

**No Docker required.** Install [Ollama](https://ollama.com), pull a model, then point the backend at it.

1. Install Ollama from [ollama.com](https://ollama.com) and start the server (e.g. `ollama serve` or run the app).
2. Pull 

*[truncated — see source for full prompt]*