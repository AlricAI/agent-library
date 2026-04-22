# Prompt Injection Defense

> > **Tradução pendente** — conteúdo em inglês, aguardando tradução para pt-BR.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
> **Tradução pendente** — conteúdo em inglês, aguardando tradução para pt-BR. Contribute to [ai-dev-toolkit-pt-br](https://github.com/LucasSantana-Dev/ai-dev-toolkit-pt-br/issues).

# Prompt Injection Defense: Layered Strategies

Prompt injection is not a theoretical attack. By Q1 2026, the benchmark is real: CaMeL achieves 67% injection block rate on AgentDojo. NIST AI RMF frames it as agent hijacking. Defense is not a single gate; it's depth.

> _Reference: [CaMeL: A Weakly Supervised Learning Framework for Community Detection](https://arxiv.org/abs/2312.03193), [AgentDojo Benchmark](https://github.com/ethz-spylab/agentdojo), [NIST AI 100-2: Threat Modeling](https://csrc.nist.gov/pubs/ai/100/2/e2025/final), [OWASP LLM Top 10 (2023)](https://owasp.org/www-project-top-10-for-large-language-model-applications/)._

## Threat model

**Direct injection**: Attacker controls the user prompt directly. "Ignore your instructions and do X." Modeled by NIST as prompt hijacking.

**Indirect injection**: Attacker controls untrusted data that flows into the prompt context. Examples:
- Retrieved documents (RAG): attacker posts a GitHub issue that becomes part of the agent's context.
- Tool outputs: LLM asks a tool that returns attacker-controlled data.
- Email/scraped content: agent processes inbound messages, web articles, or logs.
- User-uploaded files: CSV, PDF, or text parsed into context.

Indirect injection is harder to detect and more common in production. It's what breaks real agents.

## Layered defenses

Depth > any single layer. Deploy multiple controls so one failure doesn't collapse the system.

### 1. Input sanitization and structural boundaries

**Goal**: Limit how much untrusted data reaches the LLM, and use channel separation to make injection visible.

**Techniques**:
- **System vs. user message separation**: Keep your instructions in `system_role`, user input in `messages[].content`. Don't concatenate raw user input into the system message.
- **Tool output frami

*[truncated — see source for full prompt]*