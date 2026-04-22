# PROMPTS

> ## Introduction

Effective prompts are the foundation of powerful AI agents. This guide teaches you how to craft system prompts that produce consisten

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Prompt Engineering Guide

## Introduction

Effective prompts are the foundation of powerful AI agents. This guide teaches you how to craft system prompts that produce consistent, high-quality results.

## Prompt Structure

### Basic Framework

```
[IDENTITY] + [CAPABILITIES] + [GUIDELINES] + [FORMAT] + [EXAMPLES]
```

### Identity

Define who/what the agent is:

```
You are a DeFi security auditor specializing in Ethereum smart contracts.
```

Clear identity creates consistent behavior and sets user expectations.

### Capabilities

List specific skills and knowledge:

```
CAPABILITIES:
- Analyze Solidity code for common vulnerabilities
- Check for reentrancy, overflow, and access control issues
- Review token economics and minting mechanisms
- Assess gas optimization opportunities
```

### Guidelines

Behavior rules and constraints:

```
GUIDELINES:
- Classify risks as Critical/High/Medium/Low
- Provide code snippets showing vulnerabilities
- Suggest specific fixes with examples
- Never guarantee 100% security
- Recommend professional audits for production code
```

### Output Format

Structure for responses:

```
FORMAT:
Security Score: [0-100]
Critical Issues: [List]
Recommendations: [Prioritized steps]
Code Examples: [Where applicable]
```

### Examples

Demonstrate desired behavior (optional but powerful):

```
EXAMPLE:
User: "Check this function for issues"
You: "Security Score: 65/100

Critical Issues:
1. Reentrancy vulnerability on line 45
   - Current: function withdraw() external { ... }
   - Fix: Add nonReentrant modifier

Recommendations:
1. Implement checks-effects-interactions pattern
2. Add reentrancy guard
3. Consider using OpenZeppelin's ReentrancyGuard"
```

## Writing Clear Prompts

### Be Specific

❌ Vague: "You help with DeFi"
✅ Clear: "You analyze yield farming strategies across Ethereum Layer 2 protocols, focusing on risk-adjusted returns"

### Use Action Verbs

✅ Analyze, Calculate, Compare, Evaluate, Recommend, Monitor, Optimize

### Set Bo

*[truncated — see source for full prompt]*