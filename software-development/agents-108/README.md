# AGENTS

> > **Aplica-se a**: Codex CLI e OpenCode — ambos leem `AGENTS.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Guia de Roteamento de Agentes

> **Aplica-se a**: Codex CLI e OpenCode — ambos leem `AGENTS.md` automaticamente.  
> Para Claude Code, combine este arquivo com `CLAUDE.md`. Arquivos `AGENTS.md` mais profundos sobrescrevem os de nível superior.

## Estratégia Multi-Modelo

Use tiers de modelo diferentes para níveis diferentes de complexidade.
Prefira rótulos de tier na guidance compartilhada e deixe os nomes exatos dos modelos na configuração local.

**OpenCode com oh-my-openagent** ([configuração de referência](../implementations/opencode/oh-my-openagent.jsonc)):

Sisyphus delega por **categoria**, não por nome de modelo. Mantenha as categorias de roteamento estáveis e deixe a configuração em uso controlar o mapeamento exato entre provider e modelo.

| Agente | Tier | Uso |
|-------|------|-----|
| **Sisyphus** | Raciocínio profundo | Orquestrador padrão — planeja, delega e leva até a conclusão |
| **Hephaestus** | Raciocínio profundo | Arquitetura profunda, debugging multi-arquivo e raciocínio entre domínios |
| **Prometheus** | Raciocínio profundo | Planejamento estratégico e modo de entrevista |
| **Oracle** | Raciocínio profundo | Consulta de arquitetura e análise de trade-offs |
| **Librarian** | Raciocínio profundo | Busca em documentação, referência de código e lookup de patterns |
| **Atlas** | Equilibrado | Orquestração de TODOs e execução paralela |
| **Sisyphus-Junior** | Equilibrado | Subtarefas delegadas por Sisyphus |
| **Explore** | Rápido | Grep rápido no codebase e lookups pontuais |

| Categoria | Tier | Disparo |
|----------|------|---------|
| `visual-engineering` | Especialista visual | UI/UX, CSS, design, animação |
| `ultrabrain` | Raciocínio profundo | Arquitetura profunda, raciocínio complexo |
| `deep` | Raciocínio profundo | Pesquisa autônoma, investigação detalhada |
| `artistry` | Especialista visual ou criativo | Abordagens criativas ou não convencionais |
| `writing` | Equilibrado | Docs, CHANGELOG, README, prosa |
| `quick` | Rápido

*[truncated — see source for full prompt]*