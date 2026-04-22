# Agent Sandboxing

> Coding agents executam comandos reais.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Sandbox de Agents

Coding agents executam comandos reais. Agents de coding de produção, em algum ponto, tentarão fazer algo destrutivo — injeção de prompt intencional, `rm` alucinado, refatoração muito agressiva, exfiltração de dados via curl. Sandboxe o raio de impacto antes que importe, não depois.

> _Pattern informado pelo trabalho ai-jail de Fabio Akita ([akitaonrails.com](https://akitaonrails.com)), que evoluiu de um script shell bubblewrap de 170 linhas para um binário Rust com config por projeto e primitivas de sandbox multiplataforma._

## Quando sandboxar

Nem toda execução de agent precisa de um sandbox. Use essa heurística:

- **Sandbox obrigatório**: o agent pode executar shell, escrever arquivos fora do repo, abrir conexões de rede ou tocar qualquer caminho compartilhado com outros projetos.
- **Sandbox desejável**: o agent apenas lê o repo e emite texto (comentários de review, resumos).
- **Pular**: Q&A puro sem acesso a ferramentas.

O custo de sandboxing é latência de startup + configuração. O custo de não sandboxar é um prompt ruim a distância do impacto em produção. Padrão para "on" para qualquer sessão com autonomia ativada.

## O que um sandbox deve garantir

1. **Escopo do filesystem** — lista de permissão explícita de caminhos que o agent pode ler/escrever. Tudo fora é invisível (sem bind mount) ou read-only. Sem `$HOME` por padrão.
2. **Controle de egresso de rede** — negar tudo por padrão, lista de permissão dos registries + APIs que o agent realmente precisa.
3. **Isolamento de processos** — sem acesso ao `/proc` do host, `/dev` apenas com dispositivos necessários, sem namespace de PID do host.
4. **Estado de trabalho efêmero** — tmpfs para `/tmp` para que crashes/escapes não deixem traços.
5. **Firewall de credenciais** — `.env`, chaves SSH, arquivos de credenciais na nuvem **nunca** montados. Se o agent precisa de um secret, passe explicitamente via env var após uma decisão humana.

## Primitivas para construir em cima

- **Linux**: `bu

*[truncated — see source for full prompt]*