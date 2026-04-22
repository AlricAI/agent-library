# Ucai

> [**Universal Crypto MCP API Reference v1.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
[**Universal Crypto MCP API Reference v1.0.0**](../../../index.md)

***

[Universal Crypto MCP API Reference](/docs/api/index.md) / agents/ucai/src/ucai

# agents/ucai/src/ucai

## Classes

### UCAIAgent

Defined in: [agents/ucai/src/ucai.ts:51](https://github.com/nirholas/universal-crypto-mcp/blob/2b24f56f5c1847dd14a50a618b98164e511a842f/packages/agents/ucai/src/ucai.ts#L51)

#### Constructors

##### Constructor

```ts
new UCAIAgent(config: UCAIConfig): UCAIAgent;
```

Defined in: [agents/ucai/src/ucai.ts:62](https://github.com/nirholas/universal-crypto-mcp/blob/2b24f56f5c1847dd14a50a618b98164e511a842f/packages/agents/ucai/src/ucai.ts#L62)

###### Parameters

| Parameter | Type |
| :------ | :------ |
| `config` | [`UCAIConfig`](/docs/api/agents/ucai/src/ucai.md#ucaiconfig) |

###### Returns

[`UCAIAgent`](/docs/api/agents/ucai/src/ucai.md#ucaiagent)

#### Methods

##### emergencyStop()

```ts
emergencyStop(): Promise<void>;
```

Defined in: [agents/ucai/src/ucai.ts:282](https://github.com/nirholas/universal-crypto-mcp/blob/2b24f56f5c1847dd14a50a618b98164e511a842f/packages/agents/ucai/src/ucai.ts#L282)

Emergency kill switch - stops all operations

###### Returns

`Promise`\<`void`\>

##### executeChainOperation()

```ts
executeChainOperation<T>(
   chain: string, 
   action: AgentAction, 
executor: () => Promise<T>): Promise<T>;
```

Defined in: [agents/ucai/src/ucai.ts:150](https://github.com/nirholas/universal-crypto-mcp/blob/2b24f56f5c1847dd14a50a618b98164e511a842f/packages/agents/ucai/src/ucai.ts#L150)

Execute a chain operation with full safety features

###### Type Parameters

| Type Parameter |
| :------ |
| `T` |

###### Parameters

| Parameter | Type |
| :------ | :------ |
| `chain` | `string` |
| `action` | `AgentAction` |
| `executor` | () => `Promise`\<`T`\> |

###### Returns

`Promise`\<`T`\>

##### getCapabilities()

```ts
getCapabilities(): string[];
```

Defined in: [agents/ucai/src/ucai.ts:139](https://github.com/nirholas/universal-crypto-mcp/blo

*[truncated — see source for full prompt]*