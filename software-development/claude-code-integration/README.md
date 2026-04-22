# CLAUDE CODE INTEGRATION

> *For users who work entirely within Claude Code interface*

## 🤔 The Problem

You've got all these great context engineering tools, but you're not ru

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Using Context Engineering in Claude Code - Simple Guide

*For users who work entirely within Claude Code interface*

## 🤔 The Problem

You've got all these great context engineering tools, but you're not running terminal commands - you're working directly in Claude Code. How do you actually use this stuff?

## ✅ The Solution

The context engineering system can be triggered and used directly through Claude Code by simply **asking for it** in your messages. Here's how:

## 🎯 How to Use Each Feature

### 1. Meta-Clarification (Bidirectional AI Assistance)

**When**: Claude asks you clarification questions and you want to give much better responses

**The Problem**: You give Claude 20 words, Claude gives unclear responses. ChatGPT gives 500 structured words, Claude gives amazing responses.

**What to say**:
```
"Generate a meta-clarification prompt for these questions so I can get help crafting a better response"
```

**What happens**:
- Claude generates a prompt specifically designed to help you craft detailed responses
- You copy/paste it to ChatGPT or another Claude instance
- You get a structured 400-600 word response to paste back to Claude Code
- Claude gets the detailed context it needs for excellent assistance

**Example**:
```
You: "optimize the authentication system"
Claude: "I need clarification on OAuth vs JWT, user scale, security requirements..."
You: "Generate a meta-clarification prompt for these questions"
Claude: [Generates prompt asking external AI to help you craft detailed responses]
You: [Paste to ChatGPT, get structured 500-word response]
You: [Paste ChatGPT's detailed response back to Claude]
Claude: [Provides excellent implementation with full context]
```

### 2. Token Optimization

**When**: You're working with large codebases or complex contexts

**What to say**:
```
"Optimize the context for token efficiency before we continue"
```

**What happens**:
- Claude automatically compresses and optimizes the context
- Offloads less important in

*[truncated — see source for full prompt]*