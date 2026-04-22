# Memory Systems

> > Toda sessão deveria tornar a próxima melhor.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Sistemas de Memória

> Toda sessão deveria tornar a próxima melhor.

## O Problema

Você explica a mesma coisa para a IA toda segunda-feira. “Usamos trunk-based development.” “O middleware de auth está neste arquivo.” “Não faça mock do banco em testes de integração.” Sem memória persistente, toda sessão começa do zero.

## O Pattern

### Três Camadas de Memória

```
┌─────────────────────────────────────────────┐
│  Camada 1: Contexto estático (sempre lido) │
│  CLAUDE.md, .cursorrules, AGENTS.md        │
│  → Regras do projeto, arquitetura, comandos│
├─────────────────────────────────────────────┤
│  Camada 2: Memória dinâmica (sob demanda)  │
│  Arquivos de memória, decisões, padrões    │
│  → O que foi feito, por quê, o que evitar  │
├─────────────────────────────────────────────┤
│  Camada 3: Estado da sessão (efêmero)      │
│  Histórico da conversa, contexto atual     │
│  → Descartado quando a sessão termina      │
└─────────────────────────────────────────────┘
```

### O que lembrar

| Tipo de memória | Exemplo | Onde armazenar |
|-------------|---------|---------------|
| **Preferências do usuário** | “Nunca adicione co-authored-by em commits” | Memória global |
| **Feedback** | “Não faça mock do DB — isso já nos queimou” | Memória do projeto |
| **Decisões** | “Escolhemos Supabase em vez de Firebase por causa de RLS” | Memória do projeto |
| **Referências** | “Bugs do pipeline estão no projeto Linear INGEST” | Memória do projeto |
| **Gotchas** | “pre-commit roda type-check do monorepo inteiro, use HUSKY=0 para docs” | Arquivo de regras do projeto |

### O que NÃO lembrar

- Patterns de código (leia do codebase atual)
- Histórico do Git (use `git log` / `git blame`)
- Soluções de debugging (a correção está no código, o contexto está no commit)
- Detalhes efêmeros da tarefa atual (a sessão atual já lida com isso)

### Estrutura de Arquivos de Memória

```
.claude/memory/          # ou .serena/memories/, .cursor/context/
  MEMORY.md              ← Índice 

*[truncated — see source for full prompt]*