# Spec

> **目标:** 构建一个基于 Node.js (NestJS) 的高性能、零依赖、支持多模型协作的企业级 Agent 上下文管理系统。
**核心约束:** 无 LangChain，无独立 Router，环境变量驱动模型配置，基于 LLM 的 Rerank 机制。

## 1. 项目基础架构 (Inf

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 📘 Nexus-Context v2.0 技术实施规范

**目标:** 构建一个基于 Node.js (NestJS) 的高性能、零依赖、支持多模型协作的企业级 Agent 上下文管理系统。
**核心约束:** 无 LangChain，无独立 Router，环境变量驱动模型配置，基于 LLM 的 Rerank 机制。

## 1. 项目基础架构 (Infrastructure)

### 1.1 目录结构 (Directory Structure)

遵循 NestJS 标准模块化结构。

```text
src/
├── app.module.ts
├── main.ts
├── common/
│   ├── config/              # 环境变量验证
│   ├── constants/           # 系统常量
│   └── utils/               # XML构建工具, Token计算器
├── modules/
│   ├── core/
│   │   ├── prisma/          # DB 连接
│   │   └── llm-client/      # 手写 HTTP LLM 客户端 (无 LangChain)
│   ├── memory/
│   │   ├── vector-store/    # pgvector 原始 SQL 操作
│   │   ├── queue/           # BullMQ 处理器 (摘要/折叠)
│   │   └── memory.service.ts
│   └── agent/
│       ├── context/         # 上下文组装, Rerank 逻辑
│       ├── agent.controller.ts
│       └── agent.orchestrator.ts

```

### 1.2 环境变量 (Environment Variables)

使用 `zod` 或 `joi` 在启动时严格验证以下变量：

```env
# Server
PORT=3000
NODE_ENV=production

# Database
DATABASE_URL="postgresql://user:password@localhost:5432/nexus_db?schema=public"
REDIS_URL="redis://localhost:6379"

# Model 1: Thinking (主推理模型: GPT-4o, Claude 3.5 Sonnet, DeepSeek V3)
THINKING_MODEL_NAME="gpt-4o"
THINKING_MODEL_KEY="sk-..."
THINKING_MODEL_BASE="https://api.openai.com/v1"

# Model 2: Fast (高吞吐模型: GPT-4o-mini, Gemini Flash)
FAST_MODEL_NAME="gpt-4o-mini"
FAST_MODEL_KEY="sk-..."
FAST_MODEL_BASE="https://api.openai.com/v1"

# Model 3: Rerank (重排模型，通常复用 Fast 或特定小模型)
RERANK_MODEL_NAME="gpt-4o-mini"
RERANK_MODEL_KEY="sk-..."
RERANK_MODEL_BASE="https://api.openai.com/v1"
RERANK_ENABLED="true"                    # 是否启用 LLM Rerank（关闭时仅使用向量搜索 Top-5）

# Embedding (向量化模型)
EMBEDDING_MODEL_NAME="text-embedding-3-small"
EMBEDDING_MODEL_KEY="sk-..."
EMBEDDING_MODEL_BASE="https://api.openai.com/v1"

```

---

## 2. 数据库设计 (Database Schema)

### 2.1 Prisma Schema

必须开启 `postgresql` 的 `vector` 扩展。

```prisma
// schema.prisma

generator client {
  provider = "prisma-client-js"
  previewFeatures = ["postgresqlExtensions"]
}

da

*[truncated — see source for full prompt]*