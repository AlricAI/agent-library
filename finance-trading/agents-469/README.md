# AGENTS

> Available marketing intelligence skills for AI agents.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Karis Agent Skills

Available marketing intelligence skills for AI agents.

## Layer Cake

- **Layer 1 (Tools):** `npx @karis-ai/cli <namespace> <action>` — direct data retrieval (web, x, reddit, youtube, brand, geo, schedule, memory)
- **Layer 2 (Skills):** `npx @karis-ai/cli chat --skill <name> "prompt"` — LLM-powered domain agents
- **Layer 3 (CMO):** `npx @karis-ai/cli chat "prompt"` — full agent reasoning

For the complete tool list, run `npx @karis-ai/cli tools list`.

## Skills

### brand-intel

Analyze a brand and recommend high-leverage growth actions. Use when users provide a brand or URL for analysis, ask what marketing actions to take, want to understand their competitive position, or need help increasing visibility and traffic. Also use before running other Karis skills to establish brand context.

**Documentation:** [skills/brand-intel/SKILL.md](../skills/brand-intel/SKILL.md)

### aeo-geo

Audit your brand's AI search visibility and website GEO readiness. Supports two modes — visibility audit (are you being mentioned by AI?) and site audit (is your site optimized for AI?). Use when users ask about AI search performance, GEO/AEO scores, brand mentions in ChatGPT/Perplexity/Claude, AI crawler accessibility, llms.txt, or content optimization for generative engines.

**Documentation:** [skills/aeo-geo/SKILL.md](../skills/aeo-geo/SKILL.md)

### reddit-growth

Generate Reddit growth content including viral posts, comment strategies, and engagement plans. Use when founders or marketers want to create Reddit content for brand awareness, product launches, or community building. Works by calling Karis CLI which provides content strategy, post drafts, and engagement recommendations.

**Documentation:** [skills/reddit-growth/SKILL.md](../skills/reddit-growth/SKILL.md)

### reddit-listening

Analyze Reddit discussions for brand intelligence, competitor insights, and community sentiment. Use when users want to understand Reddit conversations about their brand, tr

*[truncated — see source for full prompt]*