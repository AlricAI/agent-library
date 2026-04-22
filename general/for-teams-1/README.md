# For Teams

> Uma base segura para governança, agnóstica a fornecedores, para Desenvolvimento Assistido por IA e fluxos orientados a Agents.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ai-dev-toolkit para Times

Uma base segura para governança, agnóstica a fornecedores, para Desenvolvimento Assistido por IA e fluxos orientados a Agents. Construída a partir de experiência em produção em 10+ repositórios, destilada em padrões portáveis que qualquer time pode adotar.

## TL;DR

**O que é** — uma biblioteca de convenções + ferramenta executável que transforma uso ad-hoc de IA em uma prática de engenharia repetível e mensurável.

**O que seu time ganha**
- Definições consistentes de skill / rule / agent nos projetos, para que ferramentas de IA se comportem do mesmo jeito independente de qual IDE ou CLI cada membro do time prefere.
- Um engine RAG local que mantém o conhecimento institucional recuperável em segundos — nenhuma perda de contexto entre sessões, nenhuma pergunta repetida.
- Specs leves por feature + roadmaps auto-gerados que substituem wikis obsoletos e desvio de Jira com uma fonte única de verdade nativa de git e viva.
- Padrões seguros: nenhum armazenamento SaaS de terceiros, nenhuma saída de dados na nuvem, toda recuperação roda localmente a partir de embeddings MiniLM em um arquivo SQLite.

**O que sua organização ganha**
- Uma camada de convenção auditável, in-repo — rules vivem em markdown, não escondidas em configurações de ferramentas.
- Uma história de conformidade: nenhuma ferramenta específica de Anthropic/OpenAI/Cursor no `main` (isso vive no branch `personal`); `main` é a superfície segura para trabalho.
- Velocidade de entrega: os skills têm opiniões sobre quando usar RAG, quando especificar, quando entregar, e quando parar. Menos churn, mais PRs entregues.

## Os três pilares

### 1. Desenvolvimento Assistido por IA (AAD)
Cada skill em `kit/core/skills/` é um playbook "como usar IA para X" — debugging, refatoração, review de código, geração de testes, migração, observabilidade. Skills são apenas markdown, então qualquer ferramenta de IA que leia docs do projeto (Claude Code, Cursor, Copilot Chat, Codex) os pega automaticame

*[truncated — see source for full prompt]*