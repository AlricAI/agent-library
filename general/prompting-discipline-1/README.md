# Prompting Discipline

> Como você faz uma pergunta ao modelo importa mais do que qual modelo você escolhe.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Disciplina de Prompting

Como você faz uma pergunta ao modelo importa mais do que qual modelo você escolhe. Duas disciplinas evitam a maioria das falhas de codificação com IA antes delas começarem.

> _Este pattern destila publicações de Fabio Akita ([akitaonrails.com](https://akitaonrails.com)), que argumenta que o verdadeiro gargalo é a comunicação, não a qualidade do modelo._

## O Prompt de Quatro Blocos

Todo pedido não-trivial para um agent de codificação deve conter quatro blocos explícitos:

| Bloco | Pergunta que ele responde |
|---|---|
| **Goal** | Qual resultado eu quero? |
| **Method** | Aproximadamente como o agent deve abordar isso? |
| **Constraints** | O que ele NÃO deve fazer? |
| **Validation** | Como sabemos que funcionou? |

Um prompt que falta qualquer um desses produz output proporcional à vagueza. "Fix this bug" (arrume este bug) recebe um blob que parece um fix; "Fix this auth bug by extending the existing guard in `auth/session.ts`, do not add a new middleware, and verify by running `npm test -- auth/`" (arrume este bug de auth estendendo o guard existente em `auth/session.ts`, não adicione um novo middleware, e verifique rodando `npm test -- auth/`) recebe um patch que pode ser aplicado.

### Template

```
Goal: <uma frase>

Method: <1-3 frases descrevendo a abordagem — qual arquivo, qual pattern, qual layer>

Constraints:
- do NOT <abordagem banida 1>
- do NOT <abordagem banida 2>
- keep <contrato existente>

Validation:
- run <comando>
- check <observável>
```

### Quando relaxar

One-liners ("rename this var", "add a console.log") não precisam da estrutura completa. A disciplina de quatro blocos entra em ação quando o pedido pode ser entendido de forma incorreta ou quando pode causar retrabalho.

### Por que funciona

- **Goal** previne o agent de otimizar para um objetivo diferente do seu.
- **Method** ancora o agent nos idiomas do seu codebase em vez da média de dados de treinamento.
- **Constraints** são o bloco de maior impacto — 

*[truncated — see source for full prompt]*