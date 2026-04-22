# Agent

> [**Universal Crypto MCP API Reference v1.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
[**Universal Crypto MCP API Reference v1.0.0**](../../../index.md)

***

[Universal Crypto MCP API Reference](/docs/api/index.md) / agents/agenti/src/agent

# agents/agenti/src/agent

## Example

```typescript
import { Agent, AgentConfig } from '@universal-crypto-mcp/agenti';

const config: AgentConfig = {
  name: 'trading-agent',
  description: 'Automated trading agent with guardrails',
  enableMetrics: true,
};

const agent = new Agent(config);

// Execute an action with guardrails
const result = await agent.executeAction(
  { type: 'swap', context: 'Token swap on Uniswap' },
  async () => performSwap(params)
);
```

## Classes

### Agents

#### Agent

Defined in: [agents/agenti/src/agent.ts:123](https://github.com/nirholas/universal-crypto-mcp/blob/2b24f56f5c1847dd14a50a618b98164e511a842f/packages/agents/agenti/src/agent.ts#L123)

Base AI Agent class with built-in guardrails, observability, and HITL support.

The Agent class provides a foundation for building AI-powered crypto agents
with enterprise-grade safety features:

- **Guardrails**: Validate actions before execution
- **HITL**: Human-in-the-loop approval for sensitive operations  
- **Metrics**: Prometheus-compatible observability
- **Logging**: Structured logging for debugging

 Agent

##### Example

```typescript
const agent = new Agent({
  name: 'trading-bot',
  enableMetrics: true,
});

// Execute with automatic guardrail checking
const result = await agent.executeAction(
  { type: 'transfer', context: 'Send 1 ETH' },
  async () => wallet.sendTransaction(tx)
);
```

##### Constructors

###### Constructor

```ts
new Agent(config: AgentConfig): Agent;
```

Defined in: [agents/agenti/src/agent.ts:132](https://github.com/nirholas/universal-crypto-mcp/blob/2b24f56f5c1847dd14a50a618b98164e511a842f/packages/agents/agenti/src/agent.ts#L132)

###### Parameters

| Parameter | Type |
| :------ | :------ |
| `config` | [`AgentConfig`](/docs/api/agents/agenti/src/agent.md#agentconfig) |

###### Returns

[`Agent`](

*[truncated — see source for full prompt]*