# Local First Agents

> > Data stays on your machine.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Local-First Agents

> Data stays on your machine. Latency drops to milliseconds. Cost drops to hardware amortization.

Running inference locally trades cloud vendor lock-in and subscription costs for hardware capex and operational complexity. This pattern calibrates when local LLMs win, which ones to run, and how to integrate them with your agent toolchain as of April 2026.

## Why Local?

**Cost.** A $2000 GPU pays for itself in 2-6 months if you're running Sonnet-scale reasoning 8 hours daily. After that, inference is free (amortized).

**Data sovereignty.** Code, queries, documents stay encrypted on your disk. No GDPR logs in Anthropic's backend. No surprise data use in model training.

**Latency.** Local models respond in 50-500 ms (no network round-trip). Embedding 1M documents takes hours locally, not days in cloud API batches.

**Interruptibility.** Kill the GPU job, modify the prompt, retry immediately. Cloud APIs have queue delays and rate limits.

**But: the tradeoff.** Local models lag frontier models by 3-6 months in capability (April 2026: Qwen3-Coder is production-ready; Llama 4 rumored, not shipped). Your hardware becomes a cost center; cloud APIs become elastic. Choose local only if you can justify the hardware or the workload is (latency/sovereignty)  critical.

## Model Landscape (April 2026)

| Model | Size | Best For | VRAM | Notes |
|-------|------|----------|------|-------|
| **Qwen3-Coder** | 14B/32B | Code generation, refactoring | 16GB / 32GB | Instruction-tuned, beats Sonnet on some tasks, Ollama native |
| **DeepSeek-R1-Distill** | 7B/14B/32B | Reasoning tasks, complex logic | 8GB / 16GB / 32GB | Reasoning model distilled; lower cost than raw o3 |
| **Llama 4** | 70B | General capability (if released) | 48GB+ | Rumored, not shipped as of April 2026; use Llama 3.3 (70B) instead |
| **Gemma 3** | 2B/7B/27B | Fast embeddings, routing | 8GB / 16GB | Google's model; lightweight, good for classification |
| **Mistral Large v3** | 123B | Dense 

*[truncated — see source for full prompt]*