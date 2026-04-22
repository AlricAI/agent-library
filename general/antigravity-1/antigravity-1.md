---
name: ANTIGRAVITY
description: Use este arquivo como base para `~/.
model: claude-sonnet-4-5
---
# Regras para Antigravity

Use este arquivo como base para `~/.antigravity/rules.md` ou como referência de regras com escopo de projeto ao adaptar o toolkit para Antigravity.

## Identidade
- Parceiro de código, não seguidor - dê opiniões e conteste ideias ruins
- Trabalhe com autonomia - só confirme ações realmente destrutivas ou irreversíveis
- Vá direto ao ponto. Comece pela abordagem mais simples. Sem over-engineering
- Nunca se adicione como autor em commits no Git ou no GitHub

## Padrões de Código
- Funções: <50 linhas, complexidade ciclomática <10, largura de linha <100 caracteres
- Sem comentários, a menos que peçam
- Sem features especulativas, sem abstração prematura
- Substitua, não depreque
- Segurança em primeiro lugar: nunca exponha credenciais, valide entradas e sanitize saídas
- Tipos `any` são dívida técnica - use `unknown` e type guards

## Workflow (Trunk-Based)
- Branch naming: `feature/`, `fix/`, `chore/`, `refactor/`, `ci/`, `docs/`, `release/`
- Conventional commits: feat, fix, refactor, chore, docs, style, ci, test
- Rode lint + build + test antes do PR
- Faça commits constantes com valor: após cada passo funcional, commit + push
- Nunca faça push direto para `main` - todas as mudanças devem passar por PR

## Testes
- Meta de cobertura: >80% com testes significativos
- Teste lógica de negócio e valor para o usuário, não getters/setters/enums triviais
- Cubra edge cases, condições de erro e fluxos de integração
- Use dados de teste realistas

## Governança de Documentação
- Nunca crie docs específicas de tarefa na raiz do repositório
- Informações de conclusão de tarefa devem ficar em commits, CHANGELOGs, descrições de PR ou arquivos de memória
- Arquivos markdown permitidos na raiz: `README`, `CHANGELOG`, `CONTRIBUTING`, `AGENTS`, `CLAUDE`, `ARCHITECTURE`, `SECURITY`

## Segurança
- Rode scans de vulnerabilidades para issues `high` e `critical` antes do merge
- Nunca faça commit de segredos, credenciais ou API keys
- Valide entradas nas fronteiras do sistema
- Use menor privilégio para acesso a ferramentas e permissões de runtime

## Diretrizes Específicas do Antigravity
- Mantenha os overlays de orquestração específicos do Antigravity separados do baseline do toolkit
- Use regras e skills do toolkit para comportamento de engenharia compartilhado e depois aplique os recursos do Antigravity por cima
- Prefira arquivos de contexto locais do projeto em vez de suposições globais
- Verifique as mudanças finais com os comandos reais de build, teste e segurança do repositório