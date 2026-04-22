# Litellm

> +++
date = '2025-02-24T14:13:26Z'
draft = false
title = 'LiteLLM: A Lightweight Wrapper for Multi-Provider LLMs'
categories = ['LiteLLM', 'SmartAnswer

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
+++
date = '2025-02-24T14:13:26Z'
draft = false
title = 'LiteLLM: A Lightweight Wrapper for Multi-Provider LLMs'
categories = ['LiteLLM', 'SmartAnswer']
tags = ['litellm', 'SmartAnswer']
+++

## Summary

In this post I will cover [**LiteLLM**](https://github.com/BerriAI/litellm). I used it for my implementation of [Textgrad]({{< relref "post/textgrad.md" >}}) also it was using in blog posts I did about [Agents]({{< relref "post/agents.md" >}}).

Working with multiple LLM providers is painful. Every provider has its own API, requiring custom integration, different pricing models, and maintenance overhead.
LiteLLM solves this by offering a single, unified API that allows developers to switch between OpenAI, Hugging Face, Cohere, Anthropic, and others without modifying their code.

If a provider becomes too expensive or does not support the functionality you need you can switch them out for something new.

This approach allows you to focus on your custom code and let it take care of the specifics of interfacing to different LLM providers. 

---

## Why Use LiteLLM?

### 1. **Unified API for Multiple Providers**
LiteLLM provides a consistent interface to interact with multiple LLM APIs, eliminating the need to write separate code for each provider.

### 2. **Cost Optimization**
It allows automatic fallback to cheaper or faster models when necessary, optimizing API costs and performance.

### 3. **Seamless Model Switching**
With LiteLLM, switching from one model provider to another is as simple as changing a parameter.

### 4. **Load Balancing and Routing**
LiteLLM supports model load balancing, routing requests across multiple providers for improved efficiency and availability.

### 5. **Custom Endpoints**
You can define and use custom API endpoints, making LiteLLM a great tool for self-hosted models.

---

## Getting Started with LiteLLM

### Basic Usage
To use LiteLLM, initialize it with your preferred model provider:

```python
from litellm import completion

message

*[truncated — see source for full prompt]*