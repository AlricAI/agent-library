# Src

> [**Universal Crypto MCP API Reference v1.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
[**Universal Crypto MCP API Reference v1.0.0**](../../index.md)

***

[Universal Crypto MCP API Reference](/docs/api/index.md) / agents/defi-agents/src

# agents/defi-agents/src

## Classes

### DeFiAgent

Defined in: [agents/defi-agents/src/index.ts:122](https://github.com/nirholas/universal-crypto-mcp/blob/2b24f56f5c1847dd14a50a618b98164e511a842f/packages/agents/defi-agents/src/index.ts#L122)

#### Constructors

##### Constructor

```ts
new DeFiAgent(config: DeFiAgentConfig): DeFiAgent;
```

Defined in: [agents/defi-agents/src/index.ts:129](https://github.com/nirholas/universal-crypto-mcp/blob/2b24f56f5c1847dd14a50a618b98164e511a842f/packages/agents/defi-agents/src/index.ts#L129)

###### Parameters

| Parameter | Type |
| :------ | :------ |
| `config` | [`DeFiAgentConfig`](/docs/api/agents/defi-agents/src.md#defiagentconfig) |

###### Returns

[`DeFiAgent`](/docs/api/agents/defi-agents/src.md#defiagent)

#### Methods

##### approveAction()

```ts
approveAction(
   approvalId: string, 
   reviewer: string, 
notes?: string): Promise<boolean>;
```

Defined in: [agents/defi-agents/src/index.ts:307](https://github.com/nirholas/universal-crypto-mcp/blob/2b24f56f5c1847dd14a50a618b98164e511a842f/packages/agents/defi-agents/src/index.ts#L307)

Approve a pending action

###### Parameters

| Parameter | Type |
| :------ | :------ |
| `approvalId` | `string` |
| `reviewer` | `string` |
| `notes?` | `string` |

###### Returns

`Promise`\<`boolean`\>

##### emergencyStop()

```ts
emergencyStop(): void;
```

Defined in: [agents/defi-agents/src/index.ts:277](https://github.com/nirholas/universal-crypto-mcp/blob/2b24f56f5c1847dd14a50a618b98164e511a842f/packages/agents/defi-agents/src/index.ts#L277)

Emergency stop - activates kill switch

###### Returns

`void`

##### executeAction()

```ts
executeAction(action: AgentAction): Promise<ExecutionResult>;
```

Defined in: [agents/defi-agents/src/index.ts:191](https://github.com/nirholas/universal-crypto-mcp/blob/2b24f56f5c1847dd14a50

*[truncated — see source for full prompt]*