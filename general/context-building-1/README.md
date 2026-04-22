# Context Building

> > A ação mais impactante que você pode tomar em desenvolvimento assistido por IA é dar ao agente o contexto certo antes que ele escreva uma única linha de código.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Construção de Contexto

> A ação mais impactante que você pode tomar em desenvolvimento assistido por IA é dar ao agente o contexto certo antes que ele escreva uma única linha de código.

## O Problema

Agentes de IA são tão bons quanto o contexto que recebem. Um modelo poderoso com zero contexto de projeto gera código genérico. Um modelo mediano com excelente contexto produz código que se encaixa perfeitamente no seu projeto.

## O Pattern

Todo projeto deveria ter uma **camada de contexto** — um conjunto de arquivos que qualquer agente de IA lê antes de começar a trabalhar. Os nomes dos arquivos variam por ferramenta, mas o pattern de conteúdo é universal.

### Mapeamento de Arquivos de Contexto

| Ferramenta | Arquivo principal | Arquivo secundário |
|------|-------------|----------------|
| Claude Code | `CLAUDE.md` | — |
| OpenCode | `AGENTS.md` | `CLAUDE.md` |
| Cursor | `.cursorrules` | `.cursor/rules/*.mdc` |
| GitHub Copilot | `COPILOT.md` | `.github/copilot-instructions.md` |
| Windsurf | `.windsurfrules` | — |
| Qualquer ferramenta | `CONVENTIONS.md` | — |

### O que incluir

**Sempre inclua (alto sinal):**

```markdown
# Nome do Projeto

## Referência Rápida
- Build: `npm run build`
- Teste: `npm test`
- Lint: `npm run lint`
- Dev: `npm run dev`

## Arquitetura
- Descrição breve da estrutura do projeto
- Diretórios principais e seu propósito
- Stack técnica (framework, banco, deploy)

## Padrões de Código
- Convenções de linguagem (funcional vs OOP, naming)
- Limites de tamanho de linha e de função
- Ordem de imports, organização de arquivos

## Workflow
- Convenção de nomes de branch
- Formato das mensagens de commit
- Processo de PR
```

**Nunca inclua (ruído):**
- Documentação completa da API (o agente pode ler o código)
- Listas de dependências (o agente lê `package.json`)
- Changelog histórico (o agente lê `git log`)
- Explicações em estilo tutorial

### A Regra 80/20

80% do valor do contexto vem de:
1. **Como rodar as coisas** — comandos de buil

*[truncated — see source for full prompt]*