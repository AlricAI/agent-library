# Prd

> ## 1. Visão geral

Aplicação pessoal para controle de finanças com foco em:
- **Registro completo de eventos** (compras, PIX, entradas, pagamentos de 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# PRD — App de Finanças Pessoais (Windows Desktop + Mobile via LAN) — v1.0

## 1. Visão geral

Aplicação pessoal para controle de finanças com foco em:
- **Registro completo de eventos** (compras, PIX, entradas, pagamentos de fatura, ajustes, confirmações etc.)
- **Cartões** (limite, fechamento, vencimento, faturas, parcelamentos)
- **Gastos via PIX/dinheiro**
- **Gastos fixos** (recorrentes) via **pendências** para confirmação
- **Reembolsos/terceiros** (compras no seu cartão que outra pessoa irá pagar)
- **Orçamentos por categoria**
- **Investimentos** (aportes/resgates) para controle básico
- **Visões**: geral + por mês/semana/dia
- **Desktop Windows**: inicia com Windows, fica no tray, leve
- **Mobile**: acesso via navegador **apenas na mesma rede Wi-Fi (modo LAN)**, com UI responsiva e escopo reduzido (essencial)

### Decisão de stack (reduz retrabalho)
- **UI única** em React (desktop e mobile)
- **Desktop shell**: **Tauri** (leve; usa WebView2 do Windows)
- **Backend local**: **FastAPI (Python)** + **SQLite**
- **Clean Architecture/Hexagonal** para facilitar futuro (Telegram/IA) sem duplicar regras

---

## 2. Objetivos

### 2.1 Objetivos de produto
1. Registrar transações em poucos segundos (fricção mínima).
2. Manter rastreabilidade total ("log de eventos").
3. Separar claramente:
   - **Caixa (saldo atual)**: entradas/saídas reais (PIX/dinheiro, pagamento de fatura, reembolsos recebidos)
   - **Cartão (compromissos)**: compras/parcelas alocadas em faturas por ciclo
4. Visualizar rapidamente:
   - gastos por categoria, por período
   - fatura atual e próximas
   - valores "a receber" de terceiros
   - alertas de orçamento estourado
5. Rodar leve no Windows e ficar disponível em segundo plano para integrações futuras.

### 2.2 Não objetivos (v1)
- Multiusuário real / colaboração
- Integração automática com banco/open finance
- Estornos/refunds avançados no cartão (fica para roadmap)
- Investimentos com cotação automática/rentabilidade real-time

---

## 3. U

*[truncated — see source for full prompt]*